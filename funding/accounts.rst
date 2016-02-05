Account
=======

Get a user's funding account.

Get account
-----------

::

    GET /v2/Funding/{user-id}/Account

**Response**

.. code:: json

    {
        "Status": "Open",
        "CreditLimit": 200.00,
        "AvailableCredit": 50.00,
        "Balance": 50.00,
        "PastDueBalance": 5.00,
        "NextPayment": {
            "DueDate": "2015-01-01T00:00:00Z",
            "MinimumAmount": 10.00
        },
        "ProductType": "Loan",
        "Created": "1900-01-01T00:00:00Z",
        "LastDisbursement": "1900-01-01T00:00:00Z",
        "Flags": [
            {
                "Category": "Unauthorized",
                "Reason": "LostAccess",
                "CreatedDate": "2015-02-01T12:00:00Z",
                "ExpirationDate": "2015-02-07T12:00:00Z"
            }
        ]
    }

``CreditLimit`` is the total line extended to the user.

``AvailableCredit`` is the current amount available for the user to take based upon outstanding balances.

``Balance`` is the current balance on the account based upon disbursements, payments, and fees.

**Status values:**

-  **Open** indicates that the funding account is active and the user can disburse funds.
-  **Suspended** indicates that the funding account cannot currently disburse funds because of a flag that has been put on the account.
-  **Closed** indicates that the funding account has been permanently closed.

**ProductType values:**

-  **Loan** is the standard product type.
-  **LoanETP** is an extended payment plan product.