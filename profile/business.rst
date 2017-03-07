Business
========

Retrieve and manipulate a user's business information including the business name, address, and company structure.

Get business data
-----------------

::

    GET /v2/Profile/{user-id}/Business

**Response**

.. code:: json

    {
        "Name": "Rollins' Rolls",
        "AlternativeName": "",
        "Structure": "SoleProprietorship",
        "Industry": "RestaurantsBars",
        "EntityId": "384870193",
        "DateStarted": "1990-01-01",
        "Addresses": [
            {
                "CountryCode": "US",
                "Address": {
                    "Line1": "410 Fenimore Street",
                    "Line2": "",
                    "City": "Windsor",
                    "StateCode": "VA",
                    "PostalCode": "48012"
                }
            }
        ],
        "Phones": [
            {
                "PhoneType": "Business",
                "PhoneNumber": "(555) 555-4983"
            },
            {
                "PhoneType": "Business",
                "PhoneNumber": "(555) 555-4988"
            }
        ],
        "Metadata": {
            "NumberOfEmployees": "60"
        }
    }


Fields within the ``Address`` object will vary according to the ``CountryCode`` specified.

The ``Metadata`` object is a key-value store that can hold any custom fields.


**PhoneType values**

-  Business



Update business data
--------------------

::

    PUT /v2/Profile/{user-id}/Business

**Request**

.. code:: json

    {
        "Name": "Rollins' Rolls",
        "AlternativeName": "",
        "Structure": "SoleProprietorship",
        "Industry": "RestaurantsBars",
        "EntityId": "384870193",
        "DateStarted": "1990-01-01",
        "Addresses": [
            {
                "CountryCode": "US",
                "Address": {
                    "Line1": "410 Fenimore Street",
                    "Line2": "",
                    "City": "Windsor",
                    "StateCode": "VA",
                    "PostalCode": "48012"
                }
            }
        ],
        "Phones": [
            {
                "PhoneType": "Business",
                "PhoneNumber": "(555) 555-4983"
            },
            {
                "PhoneType": "Business",
                "PhoneNumber": "(555) 555-4988"
            }
        ],
        "Metadata": {
            "NumberOfEmployees": "60"
        }
    }

**Response**

::

    HTTP/1.1 204 OK
    Content-Type: application/json;charset=UTF-8



Partially update business data
------------------------------

For partially updating the users business data the Kabbage Platform supports
`json patch <http://jsonpatch.com/>`_ requests.  This allows you to specify an
array of changes to apply.  Each change is specified as an operation, the path
to the target field, and for some operations a target value.

The following example request updates the business name, adds a new phone number
and removes the ``Line2`` value of the first address.

::

    PATCH /v2/Profile/{user-id}/Business

**Request**

.. code:: json

    [
        { "op": "add", "path": "/Name", "value": "My new business name" },
        { "op": "add", "path": "/Phones/-", "value":
            {
                "PhoneType": "Business",
                "PhoneNumber": "(555) 555-5345"
            }
        },
        { "op": "remove", "path": "/Addresses/0/Address/Line2"}
    ]

**Response**

::

    HTTP/1.1 204 OK
