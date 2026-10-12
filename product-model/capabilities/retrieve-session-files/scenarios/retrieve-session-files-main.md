---
{
  "kind": "primary",
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
      "text": "A selected main establishes the requested session.",
      "kind": "condition",
      "entities": [],
      "contexts": {
        "api": {
          "place": "claudit-api::session-files"
        }
      }
    },
    {
      "text": "The Product resolves Coding session file scope and reads the selected Transcript.",
      "kind": "product",
      "entities": [
        {
          "entity": "coding-session",
          "effect": "reads",
          "facts": [
            "Identity",
            "Main transcript availability",
            "Session file scope"
          ]
        },
        {
          "entity": "transcript",
          "effect": "reads",
          "facts": [
            "Object path",
            "Contents"
          ]
        }
      ],
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

# Session file main

## Trigger

Session-scoped source retrieval is requested.

## Outcome

The selected main file is returned as application/x-ndjson with its ETag and Cache-Control: no-cache.

## Edge cases

- The main lookup has no ordering across multiple eligible mains.
