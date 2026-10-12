---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "web-session",
      "effect": "removes",
      "contexts": [
        {
          "place": "claudit-web::public"
        },
        {
          "place": "claudit-web::authenticated"
        }
      ]
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/login.py#logout"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/session.py#resolve_session_user_id"
    }
  ],
  "permits": [
    {
      "related": [
        {
          "verb": "holds",
          "entity": "account"
        },
        {
          "verb": "has",
          "entity": "user"
        }
      ]
    },
    {
      "related": [
        {
          "verb": "holds",
          "entity": "account"
        },
        {
          "verb": "has",
          "entity": "web-operator"
        }
      ]
    },
    {
      "related": [
        {
          "verb": "holds",
          "entity": "guest"
        }
      ]
    }
  ]
}
---

# Sign-out clears presented held access

Only the presented held access is cleared. A cookie must resolve to its account before account-wide revocation is advanced; guest possession does not name another account. Cookie clearing still completes when verification or revocation storage is unavailable.
