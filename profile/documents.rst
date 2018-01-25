Documents
=========

Get document requests
---------------------

::

    GET /v2/Profile/{user-id}/DocumentRequests

**Response**

.. code:: json

    [
        {
            "DocumentRequestId": 427,
            "Status": "Open",
            "ReferenceNumber": "X-12345",
            "RequestedTypes": [
                "DriversLicense",
                "UtilityBill",
                "ArticlesOfIncorporation"
            ],
            "CreatedBy": "Steve",
            "CreatedDate": "2015-01-15T12:00:00Z",
            "RequestPurposes": []
        },
        {
            "DocumentRequestId": 378,
            "Status": "Completed",
            "ReferenceNumber": "X-45678",
            "RequestedTypes": [
                "VoidedChecks"
            ],
            "CreatedBy": "Bob",
            "CreatedDate": "2015-01-01T12:00:00Z",
            "RequestPurposes": [
                "HigherLineInput",
                "IdentityVerification",
                "AccountOwnerVerification"
            ]
        }
    ]

**Document Request Statuses**

-  **Open** - An administrator has created a request from a user, and the
   user needs to provide documents.
-  **Completed** - The user says they have completed the request. This
   is a final state.
-  **Canceled** - An administrator has manually marked the request as no
   longer needed. This is a final state.
**Document Request RequestPurposes**

-  A list of purposes tied the document request.


Update document request
-----------------------

::

    PUT /v2/Profile/{user-id}/DocumentRequests/{document-request-id}

**Request**

.. code:: json

    {
        "Status": "Completed"
    }

**Response**

HTTP Status code ``204 No Content`` for success

List available document types
-----------------------------

::

    GET /v2/Profile/{user-id}/DocumentRequests/DocumentTypes

**Response**

.. code:: json

    [
        "DriversLicense",
        "UtilityBill",
        "ArticlesOfIncorporation"
    ]

Get documents associated to document request
--------------------------------------------

::

    GET /v2/Profile/{user-id}/DocumentRequests/{document-request-id}/Documents

**Response**

.. code:: json

    [
        {
            "DocumentId": 123,
            "DocumentRequestId": 427,
            "Filename": "DriversLicense.jpg",
            "Status": "Uploaded",
            "CreatedDate": "2015-01-17T12:00:00Z",
            "DownloadUrl": "https://example.org/DriversLicense.jpg",
        },
        {
            "DocumentId": 124,
            "DocumentRequestId": 427,
            "Filename": "UtiltiyBill.jpg",
            "Status": "Created",
            "CreatedDate": "2015-01-17T12:00:00Z",
            "PutUploadUrl": "https://example.org/putUpload"
        }
    ]

**Document Request Statuses**

-  **Created** - A user has expressed the intent to upload a document
   but has not yet done so.
-  **Uploaded** - A user has successfully uploaded the document. This is
   the final state of a document.

Create document associated to document request
----------------------------------------------

::

    POST /v2/Profile/{user-id}/DocumentRequests/{document-request-id}/Documents

**Request**

.. code:: json

    {
        "Filename": "Checks.jpg"
    }

**Response**

.. code:: json

    {
        "DocumentId": 125,
        "DocumentRequestId": 427,
        "Filename": "Checks.jpg",
        "Status": "Created",
        "CreatedDate": "2015-01-17T12:00:00Z",
        "PutUploadUrl": "https://example.org/putUpload"
    }

Update status of document
-------------------------

::

    PUT /v2/Profile/{user-id}/DocumentRequests/{document-request-id}/Documents/{document-id}

**Request**

.. code:: json

    {
        "Status": "Uploaded"
    }

**Response**

HTTP Status code ``204 No Content`` for success

Get document details
--------------------

::

    GET /v2/Profile/{user-id}/DocumentRequests/{document-request-id}/Documents/{document-id}

**Response**

.. code:: json

    {
        "DocumentId": 125,
        "DocumentRequestId": 427,
        "Filename": "Checks.jpg",
        "Status": "Created",
        "CreatedDate": "2015-01-17T12:00:00Z",
        "PutUploadUrl": "https://example.org/putUpload"
    }

.. note::
    The response contract varies based upon **Status**. If the document is
    marked as **Uploaded**, the **PutUploadUrl** is replaced with a
    **DownloadUrl** containing the URL to the file.

Remove document
---------------

::

    DELETE /v2/Profile/{user-id}/DocumentRequests/{document-request-id}/Documents/{document-id}

**Response**

HTTP Status code ``204 No Content`` for success
