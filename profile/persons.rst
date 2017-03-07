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
            "Role": "PrimaryApplicant",
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
        "TaxIdNumberFull": "123459000",
        "Metadata": {
            "AtResidenceSince": "2007-10-01"
        }
    }

**Response**

::

    HTTP/1.1 204 OK
    Content-Type: application/json;charset=UTF-8



Update a person
---------------

::

    PUT /v2/Profile/{user-id}/Persons/{person-id}

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
        "TaxIdNumberFull": "123459000",
        "Metadata": {
            "AtResidenceSince": "2007-10-01"
        }
    }

**Response**

::

    HTTP/1.1 204 OK


Partially update a person
-------------------------

For partially updating the a person the Kabbage Platform supports `json patch
<http://jsonpatch.com/>`_ requests.  This allows you to specify an array of
changes to apply.  Each change is specified as an operation, the path to the
target field, and for some operations a target value.

 The following example request updates the person's first name, adds a new
phone number and removes the ``Line2`` value of the first address.

::

    PATCH /v2/Profile/{user-id}/Persons/{person-id}

**Request**

.. code:: json

    [
        { "op": "add", "path": "/Name/First", "value": "Steve" },
        { "op": "add", "path": "/Phones/-", "value":
            {
                "PhoneType": "Mobile",
                "PhoneNumber": "(555) 555-5345"
            }
        },
        { "op": "remove", "path": "/Addresses/0/Address/Line2"}
    ]

**Response**

::

    HTTP/1.1 204 OK
