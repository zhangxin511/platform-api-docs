Credit Consent
==============

A credit consent grants the Kabbage Funding Platform authorization to request a
credit report for the customer. This will generally be required for a user to
complete the application process. A partner may choose to request a new consent
from the user after some period to enable the platform to request an updated
report from their credit agency.

Create credit consent
---------------------

::

    POST /v2/Profile/{user-id}/CreditConsents

**Request**

.. code:: json

    {
        "CreditPullType": "Soft"
    }

.. note:: The value for ``CreditPullType`` varies based on the credit reporting
  agencies the partner uses and in many cases will not be required.

**Reponse**

HTTP status code ``204 No Content`` for success
