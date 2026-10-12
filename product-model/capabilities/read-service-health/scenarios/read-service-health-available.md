---
{
  "kind": "primary",
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
      "text": "The database query succeeds.",
      "kind": "condition",
      "entities": [],
      "contexts": {
        "api": {
          "place": "claudit-api::status"
        }
      }
    },
    {
      "text": "The Product returns HTTP 200 returns public version, progress, last-ingest summary and cache metadata; a prior failed ingestion does not make database status unavailable.",
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

# Health available

## Trigger

Public status is requested.

## Outcome

HTTP 200 returns public version, progress, last-ingest summary and cache metadata; a prior failed ingestion does not make database status unavailable.

## Edge cases

- Public output carries count-only object failure summaries rather than failed object addresses.
- Other listed public-status roles use the same unauthenticated contract.
