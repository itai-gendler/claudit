---
{
  "kind": "primary",
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
      "text": "Source content is unchanged, or stored parser/pricing versions are newer than this binary.",
      "kind": "condition",
      "entities": [],
      "contexts": {
        "maintenance": {
          "place": "claudit-api::maintenance"
        }
      }
    },
    {
      "text": "The Product reports unchanged work is skipped and newer stored facts are protected; clean restamping alone does not claim data changed.",
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

# Ingestion unchanged

## Trigger

Manual reconciliation is initiated.

## Outcome

Unchanged work is skipped and newer stored facts are protected; clean restamping alone does not claim data changed.

## Edge cases

- Replacement is per-file atomic, not one corpus-wide transaction.
- A fatal or aborted run skips ordinary success notification; a later successful run reconciles derived state.
- A fingerprint-only restamp does not count as changed pricing data.
