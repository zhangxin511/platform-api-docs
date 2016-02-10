Persons
=======

Get, create, and update personal information for one or more applicants.

Get persons
-----------

::

    GET /v2/Profile/{user-id}/Persons

**Response**

.. code:: json

    [
        {
            "PersonId": 12345,
            "Name": {
                "Prefix": "Mr.",
                "First": "Rollins",
                "Middle": "Steve",
                "Last": "Henderson",
                "Suffix": ""
            },
            "Addresses": [
                {
                    "CountryCode": "US",
                    "Address": {
                        "Line1": "227 Ashland Place",
                        "Line2": "",
                        "City": "Windsor",
                        "StateCode": "VA",
                        "PostalCode": "48012"
                    }
                }
            ],
            "Phones": [
                {
                    "PhoneType": "Mobile",
                    "PhoneNumber": "(555) 555-1872"
                },
                {
                    "PhoneType": "Home",
                    "PhoneNumber": "(555) 555-3483"
                }
            ],
            "BirthDate": "1965-03-12",
            "TaxIdNumberLastFour": "9000",
            "Metadata": {
                "AtResidenceSince": "2007-10-01"
            }
        }
    ]


Fields within the ``Address`` object will vary according to the ``CountryCode`` specified.

The ``Metadata`` object is a key-value store that can hold any custom fields.


**PhoneType values**

-  Home
-  Mobile
-  Fax


Create person
-------------

::

    POST /v2/Profile/{user-id}/Persons

**Request**

.. code:: json

    {
        "Name": {
            "Prefix": "Mr.",
            "First": "Rollins",
            "Middle": "Steve",
            "Last": "Henderson",
            "Suffix": ""
        },
        "Addresses": [
            {
                "CountryCode": "US",
                "Address": {
                    "Line1": "227 Ashland Place",
                    "Line2": "",
                    "City": "Windsor",
                    "StateCode": "VA",
                    "PostalCode": "48012"
                }
            }
        ],
        "Phones": [
            {
                "PhoneType": "Mobile",
                "PhoneNumber": "(555) 555-1872"
            },
            {
                "PhoneType": "Home",
                "PhoneNumber": "(555) 555-3483"
            }
        ],
        "BirthDate": "1965-03-12",
        "TaxIdNumberLastFour": "9000",
        "Metadata": {
            "AtResidenceSince": "2007-10-01"
        }
    }

**Response**

::

    HTTP/1.1 204 OK
    Content-Type: application/json;charset=UTF-8



Update person
-------------

::

    PATCH /v2/Profile/{user-id}/Persons/{person-id}

**Request**

.. code:: json

    {
        "Name": {
            "Prefix": "Mr.",
            "First": "Rollins",
            "Middle": "Steve",
            "Last": "Henderson",
            "Suffix": ""
        },
        "Addresses": [
            {
                "CountryCode": "US",
                "Address": {
                    "Line1": "227 Ashland Place",
                    "Line2": "",
                    "City": "Windsor",
                    "StateCode": "VA",
                    "PostalCode": "48012"
                }
            }
        ],
        "Phones": [
            {
                "PhoneType": "Mobile",
                "PhoneNumber": "(555) 555-1872"
            },
            {
                "PhoneType": "Home",
                "PhoneNumber": "(555) 555-3483"
            }
        ],
        "BirthDate": "1965-03-12",
        "TaxIdNumberLastFour": "9000",
        "Metadata": {
            "AtResidenceSince": "2007-10-01"
        }
    }

**Response**

::

    HTTP/1.1 204 OK
    Content-Type: application/json;charset=UTF-8