Registering Users
=================

Registering a new user
----------------------

If the Kabbage Platform is managing user credentials you can register new users
by providing a username and password. This endpoint requires tokens created
using the :ref:`client-credentials-grant` grant flow. After creating the user you
can use the token endpoint with the :ref:`password-grant` flow to get an access
token.

**Request**

::

    POST /auth/register HTTP/1.1
    Authorization: Bearer TOKEN
    Content-Type: application/json

.. code:: json

    {
        "username": "USERNAME",
        "password": "PASSWORD"
    }

**Response**

::

    HTTP/1.1 204 No Content
