Transactions
============

Get transactions
----------------

.. http:get:: /v2/Funding/(user_id)/Transactions

    **Request**

    .. sourcecode:: http

        GET /v2/Funding/{user-id}/Transactions?StartDate=2016-01-01&EndDate=2016-03-01&PageSize=50

    :query StartDate: Find transactions after this date and time. Default is 90 days before current UTC date and time.
    :query EndDate: Find transactions before this date and time. Default is Current UTC date and time.
    :query PageSize: Number of transactions to be returned, maximum of 500. Default is 100.
    
    .. note::
        ``StartDate`` and ``EndDate`` will have a default time of ``00:00:00`` if a time is not provided in the request.
    
    **Response**:

    .. sourcecode:: http

        HTTP/1.1 200 OK
        Content-Type: application/json;charset=UTF-8
        Link: <https://api.kabbage.io/v2/Funding/.../Transactions...>; rel="next"

        [
            {
                "Amount": 25.00,
                "Date": "2014-08-29T00:00:00Z",
                "Fee": 0,
                "Status": "Posted",
                "Type": "Payment",
                "Description": "Loan Payment",
                "MoneyMovementAccountId": 5432,
                "Balance": 125.00
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
                "TermLength": 12,
                "Balance": 150.00
            }
        ]

    :statuscode 403: the user does not have a funding account.
    :>jsonarr decimal FeeRate: only provided for **Disbursement** transactions.
    :>jsonarr int TermLength: only provided for **Disbursement** transactions.

    :resheader Link: provides a "next" link to facilitate paging. Requesting the supplied URL will return the next page of transactions with the same page size if any more exist. If no transactions match the given request an empty array will be returned.