Get Access Token
================

Getting an Access Token
-----------------------

The API supports the `Client Credentials`_ grant type for all clients. If the
Kabbage Platform is managing user credentials for a client then the `Resource
Owner Password Credentials`_ grant type is also supported. When applicable a
refresh token will be included with the access token response. The refresh token
may be used to `request a new access token
<http://tools.ietf.org/html/rfc6749#section-6>`_ when the access token expires.

When a client is registered for the Kabbage Platform API you will be provided a
client ID and client secret. When requesting access tokens the client ID and
client secret should be sent using `HTTP basic authentication
<https://tools.ietf.org/html/rfc2617#section-2>`_, using the client ID as the
username and the client secret as the password.  If the client is unable to use
basic authentication, the client ID and client secret may be included in the
request body as ``client_id`` and ``client_secret``.

.. _client-credntials-grant:

Client Credentials
~~~~~~~~~~~~~~~~~~

When using the client credentials grant type, the client ID and client secret
are exchanged for an access token.

The access tokens provided when using the client credentials grant are not linked
to a specific user and may be used to access the APIs on behalf of any of a
client's users.

**Request**

::

    POST /auth/token HTTP/1.1
    Authorization: Basic Q0xJRU5UX0lEOkNMSUVOVF9TRUNSRVQ=
    Content-Type: application/x-www-form-urlencoded

    grant_type=client_credentials

**Response**

::

    HTTP/1.1 200 OK
    Content-Type: application/json;charset=UTF-8

.. code:: json

    {
        "access_token": "ACCESS_TOKEN",
        "token_type": "bearer",
        "expires_in": 86399
    }

.. _password-grant:

Resource Owner Password Credentials
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

When using the resource owner password credentials grant type the client will
collect the user name and password from the user and provide them to the API in
exchange for an access token and refresh token.

The access tokens provided when using the resource owner password credentials
grant are linked to a specific user and may only be used to access the APIs on
behalf of that user.

**Request**

::

    POST /auth/token HTTP/1.1
    Authorization: Basic Q0xJRU5UX0lEOkNMSUVOVF9TRUNSRVQ=
    Content-Type: application/x-www-form-urlencoded

    grant_type=password&username=USERNAME&password=PASSWORD

**Response**

::

    HTTP/1.1 200 OK
    Content-Type: application/json;charset=UTF-8

.. code:: json

    {
        "access_token": "ACCESS_TOKEN",
        "refresh_token": "REFRESH_TOKEN"
        "token_type": "bearer",
        "expires_in": 86399
    }

.. _refresh-grant:

Refresh Tokens
~~~~~~~~~~~~~~

A refresh token will be returned with your access token if the grant type used
supports them.  This refresh token can be used to request a new access token
when the original one expires.

**Request**

::

    POST /auth/token HTTP/1.1
    Authorization: Basic Q0xJRU5UX0lEOkNMSUVOVF9TRUNSRVQ=
    Content-Type: application/x-www-form-urlencoded

    grant_type=refresh_token&refresh_token=REFRESH_TOKEN

**Response**

::

    HTTP/1.1 200 OK
    Content-Type: application/json;charset=UTF-8

.. code:: json

    {
        "access_token": "ACCESS_TOKEN",
        "refresh_token": "REFRESH_TOKEN"
        "token_type": "bearer",
        "expires_in": 86399
    }
