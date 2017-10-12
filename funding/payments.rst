Payments
========

Initiate payment
----------------

::

    POST /v2/Funding/{user-id}/Payment

**Request**

.. code:: json

    {
        "Amount": 25.00,
        "CallbackUrl": "http://your.domain.com/callback",
        "MoneyMovementAccountId": 1
    }

**Response**

HTTP status code will be ``200 OK`` if the transaction is now complete and no
redirect is required. If you need to redirect the user to complete the
transaction, the response code will be ``202 Accepted`` with a response body
containing a ``RedirectUrl`` field.  In both cases a ``PaymentToken`` will be
included in the response.  This can be used to retrieve the status of the
payment.

.. code:: json

    {
        "PaymentToken": "f9c17928-5587-4da9-babb-941796efd8f5",
        "RedirectUrl": "https://services.kabbage.com"
    }

If a previously submitted payment is still processing you may receive a ``409
Conflict`` response.

Get payment status
------------------

::

    GET /v2/Funding/{user-id}/Payment/{payment-token}

**Response**

.. code:: json

    {
        "Status": "Success"
    }

The ``Status`` will be one of the following:

 - **Success** - The transaction has completed successfully
 - **Incomplete** - The user has not completed the authorization flow on the
   provider site after following the redirect provided by the initiate payment
   response.
 - **Error** - The transaction failed to complete. An ``ErrorMessage`` field
   will  be included in the response indicating the issue.
