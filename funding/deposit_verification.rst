Micro-Deposit Verification
==========================

Get verification status
-----------------------

**Request**

::

    GET /v2/Funding/{user-id}/DepositVerification/{money-movement-account-id}

**Response**

.. code:: json

    {
        "Status": "NotVerified",
        "LastAttempt": false,
    }

**Status values:**

- **NotVerified**: The user has not yet provided the correct micro-deposit
  values for this account. They may call the verify endpoint to submit amounts.
- **Verified**: The user has provided the correct values, no further interaction
  is required.
- **MaximumAttemptsExceeded**: The user provided the wrong values and has
  exhausted their available attempts. Requests to the verify endpoint will be
  rejected.
- **NotApplicable**: The specified money movement account does not need to have
  micro-deposit verification performed.

Verify deplosit amounts
-----------------------

**Request**

::

    POST /v2/Funding/{user-id}/DepositVerification/{money-movement-account-id}/verify
    Content-Type: application/json

.. code:: json

    {
        "Amount1": 0.12,
        "Amount2": 0.54
    }

**Response**

.. code:: json

    {
        "Status": "NotVerified",
        "LastAttempt": false,
    }
