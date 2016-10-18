Terms
=====

Get terms
---------

::

    GET /v2/Funding/{user-id}/Terms

**Reponse**

.. code:: json

    [
        {
            "TermId": 123,
            "Product": "kabbage6",
            "Length": 6,
            "FeeRate": 0.04,
            "MinimumDisbursementAmount": 
        },
        {
            "TermId": 124,
            "Product": "kabbage12",
            "Length": 12,
            "FeeRate": 0.03,
            "MinimumDisbursementAmount": 5000.00
        },
    ]

''MinimumDisbursementAmount'' is a nullable value representing the minimum amount which can be requested per ''Product''

Get payment schedule for new loan
---------------------------------

::

    GET /v2/Funding/{user-id}/Terms/{term-id}/PaymentSchedule?amount=[amount]

**Response**

.. code:: json

    {
        "Payments": [
            {
                "PaymentDate": "2016-08-30",
                "PrincipalAmount": 166.67,
                "InterestFee": 40,
                "FeeRate": 0.04
            },
            {
                "PaymentDate": "2016-09-30",
                "PrincipalAmount": 166.67,
                "InterestFee": 40,
                "FeeRate": 0.04
            },
            {
                "PaymentDate": "2016-10-30",
                "PrincipalAmount": 166.67,
                "InterestFee": 10,
                "FeeRate": 0.01
            },
            {
                "PaymentDate": "2016-11-30",
                "PrincipalAmount": 166.67,
                "InterestFee": 10,
                "FeeRate": 0.01
            },
            {
                "PaymentDate": "2016-12-30",
                "PrincipalAmount": 166.67,
                "InterestFee": 10,
                "FeeRate": 0.01
            },
            {
                "PaymentDate": "2017-01-30",
                "PrincipalAmount": 166.65,
                "InterestFee": 10,
                "FeeRate": 0.01
            }
        ]
    }
