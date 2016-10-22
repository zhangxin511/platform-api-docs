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
-  **Failed** - Verification failed.
-  **ReattemptRequired** - Verification with partial tax ID failed and
   needs to be reattempted with full tax ID.

Initiate identity verification
------------------------------

::

    POST /v2/Profile/{user-id}/Persons/{person-id}/Verification/Initiate

**Response**

.. code:: json

    {
        "Id": "13a0f730-fa90-41c8-a1e3-d08adfdc7023",
        "Result": "RequiresQuestions",
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

**Result**

-  **Success** - Identity verification succeeded.
-  **RequiresQuestions** - User needs to answer questions to complete verification.
-  **NotFound** - User was not found based upon specified personal information. The user should update their personal information and reattempt verification.
-  **Failed** - User failed identity verification.

Submit challenge question answers
---------------------------------

::

    POST /v2/Profile/{user-id}/IdentityVerification/ChallengeQuestions

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
