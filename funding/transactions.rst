Transactions
============

Get transactions
----------------

::

    GET /v2/Funding/{user-id}/Transactions?NumberOfDays=[numberOfDays]

**Request Parameters**

+--------------+----------------------------------------------------------------------+
| Parameter    | Description                                                          |
+==============+======================================================================+
| NumberOfDays | How many days of transactions to retrieve (max: ???). Default = 30   |
+--------------+----------------------------------------------------------------------+


**Response**

.. code:: json

    [
        {
            "Amount": 25.00,
            "Date": "2014-08-29T00:00:00Z",
            "Fee": 0,
            "Status": "Posted",
            "Type": "Payment",
            "Description": "Loan Payment",
            "MoneyMovementAccountId": 5432
        },
        {
            "Amount": 25.00,
            "Date": "2014-08-29T00:00:00Z",
            "Fee": 0,
            "Status": "Posted",
            "Type": "Disbursement",
            "Description": "Loan Disbursement",
            "MoneyMovementAccountId": 5432,
            "FeeRate": 0.04,
            "TermLength": 12
        }
    ]

.. note::
    ``FeeRate`` and ``TermLength`` are only provided for ``Disbursement`` transactions.

Get single transaction
----------------------

::

    GET /v2/Funding/{user-id}/Transactions/{reference-id}

.. code:: json


    {
        "Amount": 25.00,
        "Date": "2014-08-29T00:00:00Z",
        "Fee": 0,
        "Status": "Posted",
        "Type": "Disbursement",
        "Description": "Loan Disbursement",
        "MoneyMovementAccountId": 5432,
        "FeeRate": 0.04,
        "TermLength": 12
    }