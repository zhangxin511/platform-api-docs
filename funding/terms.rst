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
            "FeeRate": 0.04
        },
        {
            "TermId": 124,
            "Product": "kabbage12",
            "Length": 12,
            "FeeRate": 0.03
        },
    ]


Get payment schedule for new loan
---------------------------------

::

    GET /v2/Funding/{user-id}/Terms/{term-id}/PaymentSchedule?amount=[amount]

**Response**

.. code:: json

    {
      "Payments": [
        {
          "PaymentDate": "2014-12-09",
          "PrincipalAmount": 500,
          "InterestFee": 50
        },
        {
          "PaymentDate": "2014-10-12",
          "PrincipalAmount": 500,
          "InterestFee": 50
        }
      ]
    }
