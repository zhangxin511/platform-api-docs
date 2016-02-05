Providers
=========

Get available providers
-----------------------

::

    GET /v2/Data/Providers

**Response**

.. code:: json

    [
        {
            "Name": "PayPal",
            "Roles": [
                "Payment",
                "Disbursement",
                "Data"
            ]
        },
        {
            "Name": "AuthorizeNET",
            "Roles": [
                "Data"
            ]
        },
        {
            "Name": "Acculynk",
            "Roles": [
                "Disbursement"
            ]
        }
    ]
