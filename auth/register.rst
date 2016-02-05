Registering Users
=================

Registering a new user
----------------------

If the Kabbage Platform is managing user credentials you can register new users
by providing a username and password. After creating the user you can use the
token endpoint with the :ref:`Resource Owner Password Credentials <password-grant>` flow to get an
access token.

**Request**

::

    POST /auth/register HTTP/1.1
    Authorization: Basic Q0xJRU5UX0lEOkNMSUVOVF9TRUNSRVQ=
    Content-Type: application/json

.. code:: json

    {
        "username": "USERNAME",
        "password": "PASSWORD"
    }

**Response**

::

    HTTP/1.1 204 No Content
