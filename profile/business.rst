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



Create business data
--------------------

::

    POST /v2/Profile/{user-id}/Business

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



Update business data
--------------------

::

    PATCH /v2/Profile/{user-id}/Business

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