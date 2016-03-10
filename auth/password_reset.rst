Changing a User's Password
==========================

Change user's password
----------------------

This endpoint is used to change a user's password if they know their current
password. This endpoint requires tokens created using the :ref:`password-grant`
grant flow.

**Request**

::

    POST /auth/password/change HTTP/1.1
    Authorization: Bearer TOKEN
    Content-Type: application/json

.. code:: json

    {
        "CurrentPassword": "PASSWORD",
        "NewPassword": "NEW PASSWORD"
    }

**Response**

    ::

        HTTP/1.1 204 No Content

If the supplied ``currentPassword`` does not match the user's current password
then the response code will be ``400 Bad Request``.

Initiate password reset
-----------------------

If the user has forgotten their password, this endpoint can be used to create a
password reset token that will be sent to the user which will allow them to set
a new password. This endpoint requires tokens created using the
:ref:`client-credntials-grant` grant flow.

**Request**

::

    POST /auth/password/reset HTTP/1.1
    Authorization: Bearer TOKEN
    Content-Type: application/json

.. code:: json

    {
        "Username": "USERNAME"
    }

**Response**

::

    HTTP/1.1 204 No Content

Validate password reset token
-----------------------------

This endpoint can be used to validte a password reset token presented by a user.
This endpoint requires tokens created using the :ref:`client-credntials-grant`
grant flow.

**Request**

::

    POST /auth/password/reset/validate HTTP/1.1
    Authorization: Bearer TOKEN
    Content-Type: application/json

.. code:: json

    {
        "Username": "USERNAME",
        "Token": "TOKEN"
    }

**Response**

::

    HTTP/1.1 204 No Content

If the token presented is not valid the response code will be ``400 Bad
Request``.

Reset password using token
--------------------------

This endpoint can be used to use a password reset token to change a users
password. After a sucessful password reset, the token will no longer be valid.
This endpoint requires tokens created using the :ref:`client-credntials-grant`
grant flow.

**Request**

::

    POST /auth/password/reset/process HTTP/1.1
    Authorization: Bearer TOKEN
    Content-Type: application/json

.. code:: json

    {
        "Username": "USERNAME",
        "Token": "TOKEN",
        "NewPassword": "PASSWORD"
    }

**Response**

::

    HTTP/1.1 204 No Content

If the token presented is not valid the response code will be ``400 Bad
Request``.
