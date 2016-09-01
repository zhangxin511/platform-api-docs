Decision
========

The decision endpoint returns a decision result. It is protected and
requires authentication.

Retrieve most recent decision
-----------------------------

::

    GET /v2/Decision/{user-id}/Decisions

If a decison has been made for the user, the response will contain a
``Result``.

``Result`` will be one of the following:

-  **Incomplete**
-  **Processing**
-  **Accept**
-  **Decline**
-  **NotAccept**
-  **Pended**

If the user has not provided enough information for a decision to be generated,
the result will be **Incomplete** and the ``Reasons`` will be populated with
codes indicating what information is missing.

If the user has provided enough information, but a decision has not yet been
completed the result will be **Processing**  Clients should continue to check
the endpoint untill a decision is available.

In the case that ``Result`` is **NotAccept** or **Decline**, ``Reasons``
will contain one or more codes to explain the result.

``Products`` may contain one or more product offerings as a part of the
decision. Each product will contain a unique ``Code`` and will also
include ``Parameters``. The fields in ``Parameters`` are dynamic and
specific to the type of product.

**Response**

An example **Incomplete** Response:

::

    HTTP/1.1 200 OK
    Content-Type: application/json;charset=UTF-8

.. code:: json

    {
      "CreatedDate": "2016-07-26T15:15:23Z",
      "Result": "Incomplete",
      "Reasons": [
        {
          "Code": "Profile/Business"
        },
        {
          "Code": "Data/ProviderAccounts"
        },
        {
          "Code": "Profile/Persons"
        }
      ]
    }

This indicates the user needs to complete the profile business info, add a user
provider account, and create a person.  The codes roughly correlate to API
endpoints.

An example **NotAccept** Response:

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

    POST /v2/Decision/{user-id}/Decisions/Flags/{id}/Clear

Provides the ability to clear decision flag.

**Response**

::

    HTTP/1.1 200 OK
    Content-Type: application/json;charset=UTF-8
