Disbursements
=============

.. _disbursement-initiate:

Initiate disbursement flow
--------------------------

This endpoint is used to start the process of requesting a disbursement.  The
response indicates what the consumer must request of the user prior to issuing
the loan.

::

    POST /v2/Funding/{user-id}/Disbursement

**Request**

.. code:: json

    {
        "Amount": 1000.00,
        "TermId": 127,
        "MoneyMovementAccountId": 1452
    }

**Reponse**

The ``SignatureRequired`` property indicates an electronic signature must be
collected.

The ``Agreements`` property contains an array of documents that the user must agree
to before processing the disbursement. The ``MustDisplay`` property indicates if
the document must be presented directly. If this is ``true`` the document must be
displayed inline, otherwise a link to the document URL is acceptable.

.. code:: json

    {
        "DisbursementToken": "f9c17928-5587-4da9-babb-941796efd8f5",
        "SignatureRequired": true,
        "Agreements": [
            {
                "AgreementId": 123,
                "AgreementType": "LoanAgreement",
                "MustDisplay": true,
                "Files": [
                    {
                        "ContentType": "text/html",
                        "Url": "https://example.org/example.html"
                    },
                    {
                        "ContentType": "application/pdf",
                        "Url": "https://example.org/example.pdf"
                    }
                ]
            },
            {
                "AgreementId": 124,
                "AgreementType": "SECCIAgreemnet",
                "MustDisplay": false,
                "Files": [
                    {
                        "ContentType": "text/html",
                        "Url": "https://example.org/example2.html"
                    },
                    {
                        "ContentType": "application/pdf",
                        "Url": "https://example.org/example2.pdf"
                    }
                ]
            }
        ]
    }

.. _disbursement-complete:

Accept agreements and complete disbursement
-------------------------------------------

This endpoint should be called after calling the :ref:`Initiate
Disbursement<disbursement-initiate>` endpoint to indicate that the consumer has
signed and accepted the agreements.

::

    POST /v2/Funding/{user-id}/Disbursement/{disbursement-token}/Complete

**Request**

.. code:: json

    {
        "AcceptedAgreements": [
            {
                "AgreementId": "123"
            },
            {
                "AgreementId": "124"
            }
        ],
        "Signature": "PP",
        "CallbackUrl": "http://yourdomain.org/callback"
    }

**Response**

HTTP status code will be ``204 No Content`` if the transaction is now
complete and no redirect is required. If you need to redirect the user
to complete the transaction, the response code will be ``202 Accepted`` with a
response body containing the redirect URL.

.. code:: json

    {
        "RedirectUrl": "http://kabbage.com/redirect"
    }

If the transaction was rejected for some reason the response code will be
``402``.  The response will contain an error with details as to why the
transaction was rejected.

If the ``AcceptedAgreements`` object is missing required agreements, or
agreements are missing signatures a ``400 Bad Request`` response will be
returned with details of the missing agreements or signatures.


Get disbursement status
-----------------------

If the response from the :ref:`Complete Disbursement<disbursement-complete>`
endpoint indicated that the consumer needed to redirect the user to complete
the disbursement, this endpoint can be used to check the status of the
disbursement once the user returns.

**Request**

::

    GET /v2/Funding/{user-id}/Disbursement/{disbursement-token}

**Response**

.. code:: json

    {
        "Status": "Success"
    }

The ``Status`` will be one of the following:

 - **Success** - The transaction has completed successfully
 - **Incomplete** - Either the `complete disbursement endpoint
   <disbursement-complete>`_ has not yet been called or the user has not
   completed the authorization flow on the provider site after following the
   redirect provided by the complete disbursement response.
 - **Error** - The transaction failed to complete. An ``ErrorMessage`` field
   will  be included in the response indicating the issue.
