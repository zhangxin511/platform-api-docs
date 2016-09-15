Transactions
============

Get transactions
----------------

::

    GET /v2/Funding/{user-id}/Transactions?StartDate=2016-01-01&EndDate=2016-03-01

**Request Parameters**

+--------------+---------------------------------------------------------------+
| Parameter    | Description                                                   |
+==============+===============================================================+
| StartDate    | Find transactions after this date and time.                   |
+--------------+---------------------------------------------------------------+
| EndDate      | Find transactions before this date and time.                  |
+--------------+---------------------------------------------------------------+
| PageSize     | Number of transactions to be returned, maximum of 100.        |
+--------------+---------------------------------------------------------------+

.. note::
    ``StartDate`` and ``EndDate`` will have a default time of ``00:00:00`` if a time is not provided in the request.
	

**Response**

::

    HTTP/1.1 200 OK
    Content-Type: application/json;charset=UTF-8
    Link: <https://api.kabbage.io/v2/Funding/.../Transactions...>; rel="next"

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

The Link header provides a "next" link to facilitate paging. Requesting the
supplied URL will return the next page of transactions with the same page size
if any more exist. If no transactions match the given request an empty array
will be returned.

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
