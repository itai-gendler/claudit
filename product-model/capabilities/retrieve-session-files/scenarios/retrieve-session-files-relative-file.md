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
      "text": "A main establishes the prefix and the relative address is admitted.",
      "kind": "condition",
      "entities": [],
      "contexts": {
        "api": {
          "place": "claudit-api::session-files"
        }
      }
    },
    {
      "text": "The Product resolves Coding session file scope and fetches the admitted relative source bytes.",
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

# Session file relative file

## Trigger

Session-scoped source retrieval is requested.

## Outcome

The first readable plain or .xz candidate returns inflated source bytes. The submitted path chooses JSONL, JSON or text media type.

## Edge cases

- The main lookup has no ordering across multiple eligible mains.
- Plain storage is attempted before the same key with an xz suffix.
- FileNotFoundError, every caught ClientError including access failures, and LZMAError advance to the next candidate; exhaustion becomes missing.
- Unexpected configuration/storage exceptions remain errors.
