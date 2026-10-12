---
{
  "kind": "primary",
  "routes": {
    "overview": "Overview",
    "cache": "Cache"
  },
  "steps": [
    {
      "text": "The Guest chooses sign-out.",
      "kind": "actor",
      "entities": [],
      "actor": "guest",
      "contexts": {
        "overview": {
          "place": "claudit-web::public::overview"
        },
        "cache": {
          "place": "claudit-web::public::cache"
        }
      }
    },
    {
      "text": "Presented anonymous access is held.",
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
          "place": "claudit-web::public::overview"
        },
        "cache": {
          "place": "claudit-web::public::cache"
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
      "actor": "guest",
      "contexts": {
        "overview": {
          "place": "claudit-web::public::overview"
        },
        "cache": {
          "place": "claudit-web::public::cache"
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

# Sign out guest

## Trigger

Sign-out is selected while access is held.

## Outcome

The held guest cookie is cleared and Sign in opens.

## Edge cases

- An absent or invalid cookie is still cleared; no unrelated account is revoked.
