Offers
======

.. todo:: This doesn't really make sense in funding.

Get prequalification offers for a user.

Get current offers
------------------

::

    GET /v2/Funding/{user-id}/Offers

**Response**

::

    HTTP/1.1 200 OK
    Content-Type: application/json;charset=UTF-8

.. code:: json

    [
        {
            "OfferId": 100,
            "Limit": 10000,
            "Terms": [
                {
                    "Product": "karrot36",
                    "Length": 36,
                    "FeeRate": 0.04
                }
            ]
        },
        {
            "OfferId": 101,
            "Limit": 15000,
            "Terms": [
                {
                    "Product": "karrot60",
                    "Length": 60,
                    "FeeRate": 0.03
                }
            ]
        }
    ]

Accept offer
------------

::

    POST /v2/Funding/{user-id}/Offers/{offer-id}/Accept

**Response**

::

    HTTP/1.1 204 OK
    Content-Type: application/json;charset=UTF-8
