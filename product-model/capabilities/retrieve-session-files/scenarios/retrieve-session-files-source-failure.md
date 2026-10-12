---
{
  "kind": "edge",
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
      "text": "An uncaught storage/configuration error occurs.",
      "kind": "condition",
      "entities": [],
      "contexts": {
        "api": {
          "place": "claudit-api::session-files"
        }
      }
    },
    {
      "text": "The Product reports an uncaught storage/configuration failure remains a server error rather than a missing-file response.",
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

# Session file source failure

## Trigger

Session-scoped source retrieval is requested.

## Outcome

An uncaught storage/configuration failure remains a server error rather than a missing-file response.

## Edge cases

- The main lookup has no ordering across multiple eligible mains.
- Plain storage is attempted before the same key with an xz suffix.
- FileNotFoundError, every caught ClientError including access failures, and LZMAError advance to the next candidate; exhaustion becomes missing.
- Unexpected configuration/storage exceptions remain errors.
