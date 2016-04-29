Money Movement Accounts
=======================

Get accounts available for disbursement and/or payment.

Get money movement accounts
---------------------------

::

	GET /v2/Funding/{user-id}/MoneyMovementAccounts

**Response**

.. code:: json

	[
	  {
		"Id": 123,
		"Name": "Business Checking",
		"CreatedDate": "2015-01-01T00:00:00Z",
		"DisbursementOptions": {
			"Status": "Active",
			"IsDefault": true
		},
		"PaymentOptions": {
			"Status": "Active",
			"IsDefault": true
		}
	  },
	  {
		"Id": 125,
		"Name": "Business Checking 2",
		"CreatedDate": "2015-01-01T00:00:00Z",
		"DisbursementOptions": {
			"Status": "Unavailable",
			"IsDefault": false
		},
		"PaymentOptions": {
			"Status": "Active",
			"IsDefault": false
		}
	  }
	]


The money movement account includes a ``Status`` within the response. Enumerated values include:

-  **Active** indicates that the account is ready and eligible for disbursements or payments
-  **Suspended** indicates that disbursement or payment activity has been put on hold for this account
-  **Unavailable** indicates that this account cannot be used for disbursements or payments



Get single money movement account
---------------------------------

.. code:: json

	GET /v2/Funding/{user-id}/MoneyMovementAccounts/{money-movement-account-id}


**Response**

.. code:: json

  {
	"Id": 123,
	"Name": "Business Checking",
	"CreatedDate": "2015-01-01T00:00:00Z",
	"DisbursementOptions": {
		"Status": "Active",
		"IsDefault": true
	},
	"PaymentOptions": {
		"Status": "Active",
		"Priority": 1
	}
  }
