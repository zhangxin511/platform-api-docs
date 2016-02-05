Statements
==========

Retrieve data related to customer statements.

Get available statements
------------------------

::

    GET /v2/Funding/{user-id}/Statements

**Response**

.. code:: json

    [
        {
            "Date": "2015-01-01"
        },
        {
            "Date": "2015-02-01"
        }
    ]

Get statement details
---------------------

::

    GET /v2/Funding/{user-id}/Statements/{date}

**Response**

.. code:: json

    {
      "CustomerName": "Rollins Henderson",
      "AccountNumber": "111111******4444",
      "PreviousBalance": 0.00,
      "Purchases": 3000.00,
      "Fees": 0.00,
      "Payments": 1007.50,
      "NewBalance": 2142.50,
      "MinimumPaymentDue": 650.00,
      "PaymentDueDate": "2014-09-22",
      "BillingDate": "2014-09-02",
      "DaysInBillingCycle": 31,
      "Transactions": [
        {
          "TransactionDate": "2014-08-29",
          "ReferenceNumber": "",
          "TransactionDescription": "625 = Direct deposit loan",
          "TransactionAmount": 3000.00,
          "TransactionType": "GEN"
        }
      ]
    }
	

.. note::
    The consumer can change the response format by specifying an ``Accept``
    header with a value of ``text/html`` or ``application/pdf``.