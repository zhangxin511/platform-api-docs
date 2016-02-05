Status
======

Get Funding API status
----------------------
::

    GET /v2/Funding/Status

**Response**

.. code:: json

    {
        "Status": "LowFunctionality"
    }

**Statuses**

-  Ok - API is functioning normally
-  LowFunctionality - The following functions are disabled:
	-  Get Cash
	-  Make Payment
	-  List Transactions
	-  Get Statements
	-  Get User (Half Functional)
