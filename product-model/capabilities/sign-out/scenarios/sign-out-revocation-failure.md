---
{
  "kind": "edge",
  "routes": {
    "overview": "Overview",
    "cache": "Cache",
    "sessions": "Sessions",
    "inspector": "Inspector"
  },
  "steps": [
    {
      "text": "The User chooses sign-out.",
      "kind": "actor",
      "entities": [],
      "actor": "user",
      "contexts": {
        "overview": {
          "place": "claudit-web::authenticated::overview"
        },
        "cache": {
          "place": "claudit-web::authenticated::cache"
        },
        "sessions": {
          "place": "claudit-web::authenticated::sessions"
        },
        "inspector": {
          "place": "claudit-web::authenticated::inspector"
        }
      }
    },
    {
      "text": "Holder resolution or revocation storage is unavailable.",
      "kind": "condition",
      "entities": [
        {
          "entity": "web-session",
          "effect": "reads",
          "facts": [
            "Audience",
            "Holder",
            "Validity"
          ]
        }
      ],
      "contexts": {
        "overview": {
          "place": "claudit-web::authenticated::overview"
        },
        "cache": {
          "place": "claudit-web::authenticated::cache"
        },
        "sessions": {
          "place": "claudit-web::authenticated::sessions"
        },
        "inspector": {
          "place": "claudit-web::authenticated::inspector"
        }
      }
    },
    {
      "text": "The Product clears the held Web session and returns to Sign in.",
      "kind": "product",
      "entities": [
        {
          "entity": "web-session",
          "effect": "removes"
        }
      ],
      "actor": "user",
      "contexts": {
        "overview": {
          "place": "claudit-web::authenticated::overview"
        },
        "cache": {
          "place": "claudit-web::authenticated::cache"
        },
        "sessions": {
          "place": "claudit-web::authenticated::sessions"
        },
        "inspector": {
          "place": "claudit-web::authenticated::inspector"
        }
      }
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/login.py#logout"
    }
  ]
}
---

# Sign out revocation failure

## Trigger

Sign-out is selected while access is held.

## Outcome

The current cookie is still cleared and Sign in opens; account-wide revocation is not guaranteed.

## Edge cases

- An absent or invalid cookie is still cleared; no unrelated account is revoked.
