Authentication
==============

The Kabbage Platform API uses the `OAuth 2.0
<http://tools.ietf.org/html/rfc6749>`_ protocol for authentication. You can use
the :doc:`token endpoint<token>` to get an access token in order to make API
calls.


Making API Requests
-------------------

After a client has a valid access token you must send it with each request to
prove you are authorized. The access token is included in the ``Authorization``
HTTP header in each request in this format: ``Authorization: Bearer
ACCESS_TOKEN``.  For example:

::

    GET /data/v2/providers HTTP/1.1
    Authorization: Bearer Q0xJRU5UX0lEOkNMSUVOVF9TRUNSRVQ=

If the provided access token is invalid you will receive a ``401 Unauthorized``
response.

.. todo:: simple flow diagram
