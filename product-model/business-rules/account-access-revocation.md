---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "account",
      "effect": "changes",
      "facts": [
        "Access revocation"
      ],
      "contexts": [
        {
          "place": "claudit-web::authenticated"
        },
        {
          "place": "claudit-web::public"
        }
      ]
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/session.py#get_or_create_session_row"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/session.py#bump_session_generation"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/login.py#logout"
    }
  ],
  "permits": [
    {
      "related": [
        {
          "verb": "has",
          "entity": "user"
        }
      ]
    },
    {
      "related": [
        {
          "verb": "has",
          "entity": "web-operator"
        }
      ]
    }
  ]
}
---

# Account revocation follows admitted entry or logout

Verified entry can rotate access when its accepted credential binding differs; sign-out advances the presented account revocation. Neither operation edits external credentials. Revocation failure does not prevent current cookie clearing.
