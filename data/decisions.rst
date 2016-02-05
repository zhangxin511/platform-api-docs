Decision
========

The decision endpoint returns a decision result. It is protected and
requires authentication.

Retrieve most recent decision
-----------------------------

::

    GET /v2/Data/{user-id}/Decisions

If a decison has been made for the user, the response will contain a
``Result``.

``Result`` will be one of the following:

-  **Accept**
-  **Decline**
-  **NotAccept**
-  **Pended**

In the case that ``Result`` is **NotAccept** or **Decline**, ``Reasons``
will contain one or more codes to explain the result.

``Products`` may contain one or more product offerings as a part of the
decision. Each product will contain a unique ``Code`` and will also
include ``Parameters``. The fields in ``Parameters`` are dynamic and
specific to the type of product.

If a decision has never been made for the user, the endpoint will
respond with ``204 No Content``.

**Response**

::

    HTTP/1.1 200 OK
    Content-Type: application/json;charset=UTF-8

.. code:: json

    {
      "CreatedDate": "2018-01-01T00:00:00Z",
      "Result": "NotAccept",
      "Reasons": [
        {
          "Code": "YodleeNameMismatch"
        }
      ],
      "Products": [
        {
          "Code": "Kabbage6",
          "Parameters": {
            "...": "...",
            "...": "..."
          }
        },
        {
          "Code": "Kabbage36",
          "Parameters": {
            "Duration": "36",
            "Line": "15000",
            "Currency": "USD",
            "Tier": "2",
            "Rate": "0.05",
            "Owner": "Kabbage"
          }
        }
      ],
      "Flags": [
        {
          "Id": 12,
          "Code": "YodleeNameMismatch",
          "Cleared": false,
          "ProviderAccountId": 123
        }
      ],
      "Strategy": {
        "...": "...",
        "...": "...",
      }
    }

Clear flag
----------

::

    POST /v2/Data/{user-id}/Decisions/Flags/{id}/Clear

Provides the ability to clear decision flag.

**Response**

::

    HTTP/1.1 200 OK
    Content-Type: application/json;charset=UTF-8
