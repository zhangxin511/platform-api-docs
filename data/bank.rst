Bank
=========

The ``ACH`` provider has some enhanced functionality that is exposed through a
set of bank endpoints.

Search for banks
----------------

You can search for banks by name or by routing number. Searching by name is the
prefered method, some routing numbers may be valid but not mapped to a bank.

::

    GET /v2/Data/{user-id}/Bank/Search?Name=example%20bank

**Request Parameters**

+---------------+--------------------------------------------------------------+
| Parameter     | Description                                                  |
+===============+==============================================================+
| Name          | Search for banks containing this name.                       |
+---------------+--------------------------------------------------------------+
| RoutingNumber | Search for a bank with the given routing number.             |
+---------------+--------------------------------------------------------------+

**Response**

.. code:: json

    {
      "Banks": [
        {
          "Name": "Example Bank",
          "FormId": "12345"
        },
        {
          "Name": "Another Example Bank",
          "FormId": "12346"
        }
      ]
    }

Add bank credentials
--------------------

This endpoint allows for the adding of an account and routing number (or your
countries equivelent).

::

    POST /v2/Data/{user-id}/Bank/{provider-account-id}/Credentials

**Request**

::

	{
	  "RoutingNumber": "123456789",
	  "AccountNumber": "1234567890123"
	}

**Response**

::
    
    HTTP/1.1 204 No Content
    Content-Type: application/json;charset=UTF-8
