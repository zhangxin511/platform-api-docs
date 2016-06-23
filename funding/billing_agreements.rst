Billing Agreements
==================

A billing agreement is required for some money movement providers to allow the
Kabbage Funding Platform to collect funds without user interaction during
autodraft processing. A billing agreement will be created during the
disbursement if it is required for the provider so this endpoint is most often
used to confirm a user has the required billing agreement so that the platform
can autodraft the users account.

Get billing agreements
----------------------

**Request**

::

    GET /v2/Funding/{user-id}/BillingAgreements

**Parameters**

- ``valid``: If set to ``true`` used to filter the results to only contain
  billing agreements that can be used to collect funds (not expired or cancelled
  and has a remaining balance).

**Response**

.. code:: json

    [
        {
            "BillingAgreementId": "87BAEA1C-D842-4605-8ED4-F5EB54203267",
            "MoneyMovementAccountId": "123",
            "StartingDate": "2015-01-01T00:00:00Z",
            "EndingDate": "2015-01-01T00:00:00Z",
            "Status": "Approved",
            "RemainingBalance": 1000.00
        }
    ]

**Status values:**

- **Approved**: The user has accepted the agreement and the agreement can be
  used for processing autodraft payments.
- **Pending**: The user has not yet acceptted the agreement.
- **Cancelled**: The user accepted the agreement but later deactivated it via
  the provider.

Get single billing agreement
----------------------------

::

    GET /v2/Funding/{user-id}/BillingAgreements/{billing-agreement-id}

**Response**

::

    HTTP/1.1 200 OK
    Content-Type: application/json;charset=UTF-8

.. code:: json

    {
        "BillingAgreementId": "87BAEA1C-D842-4605-8ED4-F5EB54203267",
        "MoneyMovementAccountId": "123",
        "StartingDate": "2015-01-01T00:00:00Z",
        "EndingDate": "2015-01-01T00:00:00Z",
        "Status": "Accepted",
        "RemainingBalance": 1000.00
    }

Create billing agreement
------------------------

.. note::

    This is an unusual operation.  Normally billing agreements will be created
    during a disbursement using the :doc:`disbursements` endpoint. This
    operation may be used if the user has a remaining balance but does not have
    a valid billing agreement to resolve issues with autodraft.

::

    POST /v2/Funding/{user-id}/BillingAgreements
    Content-Type: application/json

**Request**

Creating a billing agreement may require the user to be redirected to a provider
site to authorize creating the agreement. The ``CallbackUrl`` provided in the
request will be used to send the user back to the consumer after this redirect
is complete. The ``MoneyMovementAccountId`` must refer to a provider account that
supports billing agreements (currently PayPal only).  The billing agreement
amount and date range are automatically set to the maximum allowed by the
provider.

.. code:: json

    {
        "MoneyMovementAccountId": 123,
        "CallbackUrl": "http://example.org/callback"
    }

**Response**

If a ``RedirectUrl`` is present in the response the consumer must redirect the
user to that URL to complete the billing agreement.  After the user completes
the billing agreement, they will be redirected to the ``CallbackUrl`` provided
in the request.

::

    HTTP/1.1 200 OK
    Content-Type: application/json;charset=UTF-8

.. code:: json

    {
        "BillingAgreementId": "87BAEA1C-D842-4605-8ED4-F5EB54203267",
        "RedirectUrl": "http://kabbage.io/redirect",
        "StartingDate": "2015-01-01T00:00:00Z",
        "EndingDate": "2015-01-01T00:00:00Z",
        "Status": "Accepted"
    }

If the request contained the id of a provider account that does not support
billing agreements a ``400 Bad Request`` response will be returned.
