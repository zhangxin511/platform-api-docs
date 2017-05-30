Identity Verification
=====================

.. todo:: Add flow diagrams.

Get identity verification status
--------------------------------

::

    GET /v2/Profile/{user-id}/Persons/{person-id}/Verification

**Response**

.. code:: json

    {
        "Status": "Verified"
    }

**Statuses**

-  **Unknown** - Verification has not been attempted.
-  **Verified** - Verification passed.
-  **ReattemptRequired** - Verification has failed, client may try again.
-  **Failed** - Verification failed.

Initiate identity verification
------------------------------

::

    POST /v2/Profile/{user-id}/Persons/{person-id}/Verification/Initiate

**Response**

.. code:: json

    {
        "Status": "Verified"
    }

**Statuses**

-  **Verified** - Verification passed.
-  **ReattemptRequired** - Verification has failed, client may try again.
-  **Failed** - User failed identity verification.
-  **RequiresQuestions** - User needs to answer questions to complete verification.

**ReattemptRequired**

A response with status **ReattemptRequired** indicates the client should use /v2/Profile/Persons to update
Person with better information. If only 4 digits of the TaxId have been provided, Person should be updated
with the full TaxId.

**Questions**

A response with status **RequiresQuestions** will contain a ``Questions`` array.

.. code:: json

    {
        "Id": "13a0f730-fa90-41c8-a1e3-d08adfdc7023",
        "Status": "RequiresQuestions",
        "Questions": [
            {
                "QuestionId": "1",
                "Prompt": "Which of these addresses have you lived at in the past 10 years?",
                "Answers": [
                    "111 Pumpkin Patch Ave",
                    "246 Kabbage Patch Lane",
                    "135 Turnip Patch St",
                    "None of these"
                ]
            }
        ]
    }



Submit challenge question answers
---------------------------------

::

    POST /v2/Profile/{user-id}/Persons/{person-id}/Verification/ChallengeQuestions

**Request**

.. code:: json

  {
      "Id": "13a0f730-fa90-41c8-a1e3-d08adfdc7023",
      "QuestionAnswers": [
          {
              "QuestionId": "1",
              "Answer": "246 Kabbage Patch Lane"
          }
      ]
  }
