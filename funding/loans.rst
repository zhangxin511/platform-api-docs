Loans
=====

Get loan details, activity, and related documents for a user.

Get loans
---------

::

    GET /v2/Funding/{user-id}/Loans

**Response**

.. code:: json

    [
      {
        "LoanId": 12345,
        "Status": "PaidInFull",
        "Description": "ACH Loan",
        "OriginalAmount": 2000.00,
        "Balance": 0.00,
        "DateInitiated": "2015-08-29T00:00:00Z",
        "DateClosed": "2015-10-15T00:00:00Z"
      }
    ]

**Status values:**

-  **PaidInFull** - Loan has been completely paid off.
-  **Open** - Loan is active and has a balance.



Get loan activity
-----------------

::

    GET /v2/Funding/{user-id}/Loans/{loan-id}/Activity

**Response**

.. code:: json

    [
      {
        "ActivityType": "Disbursement",
        "Date": "2015-08-29T00:00:00Z",
        "TransactionId": 1432,
        "Description": "Kabbage Loan",
        "Amount": 2000.00,
        "AppliedToPrincipal": 2000.00,
        "AppliedToInterest": 0.00,
        "AppliedToFees": 0.00
      },
      {
        "ActivityType": "Fee",
        "Date": "2015-08-29T00:00:00Z",
        "Description": "Commitment Fee",
        "Amount": 10.00,
        "AppliedToPrincipal": 0.00,
        "AppliedToInterest": 0.00,
        "AppliedToFees": 10.00
      },
      {
        "ActivityType": "Payment",
        "Date": "2015-09-28T00:00:00Z",
        "TransactionId": 1433,
        "Description": "Loan Payment",
        "Amount": 300.00,
        "AppliedToPrincipal": 280.00,
        "AppliedToInterest": 20.00,
        "AppliedToFees": 0.00
      }
    ]

**ActivityType values:**

-  **Disbursement**
-  **DisbursementReversal**
-  **Payment**
-  **PaymentReversal**
-  **Fee**
-  **FeeReversal**
-  **ChargeOff**
-  **ChargeOffReversal**
-  **ProductTransfer**
-  **Other**



Get loan documents
------------------

::

    GET /v2/Funding/{user-id}/Loans/{loan-id}/Documents

**Response**

.. code:: json

    [
      {
        "Name": "Kabbage Loan Agreement",
        "Url": "https://example.org/LoanAgreement.pdf"
      }
    ]