Consents
========

Get consents
------------

::

    GET /v2/Audit/{user-id}/Consents

**Response**

.. code:: json

    [
      {
        "ConsentId" : 1234,
        "ConsentType": "MobilePhone",
        "CreatedDate": "2015-01-01T00:00:00Z",
        "Accepted": true
      }
    ]

Create a new consent
--------------------

::

    POST /v2/Audit/{user-id}/Consents

**Request**

.. code:: json

    {
        "ConsentType": "MobilePhone",
        "Accepted": true
    }

**Reponse**

HTTP status code ``201 Created`` for success

.. code:: json

    {
      "ConsentId" : 1234,
      "ConsentType": "MobilePhone",
      "CreatedDate": "2015-01-01T00:00:00Z",
      "Accepted": true
    }