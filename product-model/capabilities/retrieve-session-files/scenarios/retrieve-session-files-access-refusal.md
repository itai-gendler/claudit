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
      "text": "Presented credentialed access is missing, invalid, expired or revoked.",
      "kind": "condition",
      "entities": [],
      "contexts": {
        "api": {
          "place": "claudit-api::session-files"
        }
      }
    },
    {
      "text": "The Product reports invalid or revoked presented access receives HTTP 401; no source bytes are disclosed.",
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

# Session file access refusal

## Trigger

Session-scoped source retrieval is requested.

## Outcome

Invalid or revoked presented access receives HTTP 401; no source bytes are disclosed.

## Edge cases

- The main lookup has no ordering across multiple eligible mains.
