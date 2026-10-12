---
{
  "kind": "edge",
  "routes": {
    "maintenance": "Maintenance"
  },
  "steps": [
    {
      "text": "The Deployment operator initiates ingestion of configured sources.",
      "kind": "actor",
      "entities": [],
      "actor": "deployment-operator",
      "contexts": {
        "maintenance": {
          "place": "claudit-api::maintenance"
        }
      }
    },
    {
      "text": "A local or database-wide ingest lock is already held.",
      "kind": "condition",
      "entities": [],
      "contexts": {
        "maintenance": {
          "place": "claudit-api::maintenance"
        }
      }
    },
    {
      "text": "The Product reports the competing attempt returns a skipped result without overlapping reconciliation or a new completed run receipt.",
      "kind": "product",
      "entities": [],
      "actor": "deployment-operator",
      "contexts": {
        "maintenance": {
          "place": "claudit-api::maintenance"
        }
      }
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/app.py#admin_ingest"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/ingest.py#run_ingest"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/ingest.py#_run_ingest_locked"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/ingest_persist.py#_persist"
    }
  ]
}
---

# Ingestion concurrent

## Trigger

Manual reconciliation is initiated.

## Outcome

The competing attempt returns a skipped result without overlapping reconciliation or a new completed run receipt.

## Edge cases

- Replacement is per-file atomic, not one corpus-wide transaction.
- A fatal or aborted run skips ordinary success notification; a later successful run reconciles derived state.
- A skipped attempt can leave the previous health row visible and need not create a new run receipt.
