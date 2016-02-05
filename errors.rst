Errors
======

Errors will be communicated via appropriate HTTP status codes and an
error response in the requested format. Special errors cases will be
documented in the endpoint documentation.

Examples
--------

Issues with the resource address will result in a ``404 Not Found``

.. code:: json

    {
        "Message": "User not found",
        "Errors": [
            {
                "Key": "User",
                "Code": "NotFound"
            }
        ]
    }

Issues with request content will result in a ``400 Bad Request``

.. code:: json

    {
        "Message": "Validation Failed",
        "Errors": [
            {
                "Key": "Profile.Personal.Address.Line1",
                "Code": "MissingField"
            }
        ]
    }

Special Error cases
-------------------

When our system of record undergoes maintenance some API functionality
will be unavailable. During these times a ``503 Service Unavailable``
response will be returned. Endpoints that are not functional during
maintenance periods will be documented.

The response body will contain the following error:

.. code:: json

    {
        "Message": "System of record is unavailable",
        "Errors": [
            {
                "Code": "SystemOfRecordUnavailable"
            }
        ]
    }
