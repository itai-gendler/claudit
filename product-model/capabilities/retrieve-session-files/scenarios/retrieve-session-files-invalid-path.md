---
{
  "kind": "validation",
  "routes": {
    "api": "Session files"
  },
  "steps": [
    {
      "text": "The User calls the documented source-file route with the selected session identifier.",
      "kind": "actor",
      "entities": [],
      "actor": "user",
      "contexts": {
        "api": {
          "place": "claudit-api::session-files"
        }
      }
    },
    {
      "text": "The Coding session has a main establishing Session file scope; the nonempty relative address starts with a slash, contains a dot/dot-dot component or NUL.",
      "kind": "condition",
      "entities": [
        {
          "entity": "coding-session",
          "effect": "reads",
          "facts": [
            "Main transcript availability",
            "Session file scope"
          ]
        }
      ],
      "contexts": {
        "api": {
          "place": "claudit-api::session-files"
        }
      },
      "actor": "user"
    },
    {
      "text": "The Product returns HTTP 400 for the invalid nonempty path before storage fetch.",
      "kind": "product",
      "entities": [],
      "actor": "user",
      "contexts": {
        "api": {
          "place": "claudit-api::session-files"
        }
      }
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/api_sessions.py#get_transcript"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/api_sessions.py#get_sidecar"
    }
  ]
}
---

# Session file invalid path

## Trigger

Session-scoped source retrieval is requested.

## Outcome

The nonempty invalid path receives HTTP 400 before storage fetch.

## Edge cases

- The main lookup has no ordering across multiple eligible mains.
- An absent or empty required path receives framework HTTP 422 before the handler reads session scope or fetches storage.
