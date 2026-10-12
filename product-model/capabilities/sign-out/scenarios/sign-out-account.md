---
{
  "kind": "primary",
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
      "text": "Presented credentialed access resolves to its bound holder.",
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
      "text": "The Product advances Account access revocation.",
      "kind": "product",
      "entities": [
        {
          "entity": "account",
          "effect": "changes",
          "facts": [
            "Access revocation"
          ]
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

# Sign out account

## Trigger

Sign-out is selected while access is held.

## Outcome

The held cookie is cleared, account-wide access is revoked and Sign in opens.

## Edge cases

- An absent or invalid cookie is still cleared; no unrelated account is revoked.
