---
{
  "kind": "edge",
  "routes": {
    "api": "Public status"
  },
  "steps": [
    {
      "text": "The Deployment operator reads public service status.",
      "kind": "actor",
      "entities": [],
      "actor": "deployment-operator",
      "contexts": {
        "api": {
          "place": "claudit-api::status"
        }
      }
    },
    {
      "text": "The database query fails.",
      "kind": "condition",
      "entities": [],
      "contexts": {
        "api": {
          "place": "claudit-api::status"
        }
      }
    },
    {
      "text": "The Product returns HTTP 503 returns ok: false, db: false and the generic database unavailable error with version/parser-version and current time.",
      "kind": "product",
      "entities": [],
      "actor": "deployment-operator",
      "contexts": {
        "api": {
          "place": "claudit-api::status"
        }
      }
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/ingest_progress.py#health"
    }
  ]
}
---

# Health unavailable

## Trigger

Public status is requested.

## Outcome

HTTP 503 returns ok: false, db: false and the generic database unavailable error with version/parser-version and current time.

## Edge cases

- Public output carries count-only object failure summaries rather than failed object addresses.
- Other listed public-status roles use the same unauthenticated contract.
