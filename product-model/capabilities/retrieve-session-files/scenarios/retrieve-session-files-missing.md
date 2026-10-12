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
      "text": "No main establishes scope, or both candidates fail under caught-error fallback.",
      "kind": "condition",
      "entities": [],
      "contexts": {
        "api": {
          "place": "claudit-api::session-files"
        }
      }
    },
    {
      "text": "The Product returns HTTP 404 reports session not found when no main establishes scope, or sidecar not found when both caught-error candidates fail.",
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

# Session file missing

## Trigger

Session-scoped source retrieval is requested.

## Outcome

HTTP 404 reports session not found when no main establishes scope, or sidecar not found when both caught-error candidates fail.

## Edge cases

- The main lookup has no ordering across multiple eligible mains.
- Plain storage is attempted before the same key with an xz suffix.
- FileNotFoundError, every caught ClientError including access failures, and LZMAError advance to the next candidate; exhaustion becomes missing.
- Unexpected configuration/storage exceptions remain errors.
