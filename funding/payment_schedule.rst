Payment Schedule
================

Get projected payment details for a user's existing loans.

Get payment schedule for existing loans
---------------------------------------

::

    GET /v2/Funding/{user-id}/PaymentSchedule

**Response**

.. code:: json

    [
      {
        "LoanId": 12702,
        "Payments": [
          {
            "PaymentDate": "2015-09-12",
            "PrincipalAmount": 500,
            "InterestFee": 50
          },
          {
            "PaymentDate": "2015-10-12",
            "PrincipalAmount": 500,
            "InterestFee": 50
          }
        ]
      },
      {
        "LoanId": 18273,
        "Payments": [
          {
            "PaymentDate": "2015-09-12",
            "PrincipalAmount": 200,
            "InterestFee": 20
          },
          {
            "PaymentDate": "2015-10-12",
            "PrincipalAmount": 200,
            "InterestFee": 20
          }
        ]
      }
    ]