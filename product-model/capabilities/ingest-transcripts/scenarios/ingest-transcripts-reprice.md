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
      "text": "Stored pricing provenance is stale for affected request facts.",
      "kind": "condition",
      "entities": [
        {
          "entity": "request",
          "effect": "reads",
          "facts": [
            "Rate classification",
            "Estimated cost"
          ]
        }
      ],
      "contexts": {
        "maintenance": {
          "place": "claudit-api::maintenance"
        }
      }
    },
    {
      "text": "The Product reprices Request cost and meter treatment from stored usage and dated rate data.",
      "kind": "product",
      "entities": [
        {
          "entity": "request",
          "effect": "changes",
          "facts": [
            "Estimated cost",
            "Rate classification",
            "Meter treatment"
          ]
        }
      ],
      "actor": "deployment-operator",
      "contexts": {
        "maintenance": {
          "place": "claudit-api::maintenance"
        }
      }
    },
    {
      "text": "The Product processes durable performance summaries before pruning retained raw Performance measurement information.",
      "kind": "product",
      "entities": [
        {
          "entity": "performance-measurement",
          "effect": "removes"
        }
      ],
      "actor": "deployment-operator",
      "contexts": {
        "maintenance": {
          "place": "claudit-api::maintenance"
        }
      }
    },
    {
      "text": "The Product reports revised stored costs and meter treatment without refetching source objects.",
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

# Ingestion reprice

## Trigger

Manual reconciliation is initiated.

## Outcome

Costs and applicable meter treatment are recomputed without transcript fetches.

## Edge cases

- Replacement is per-file atomic, not one corpus-wide transaction.
- A fatal or aborted run skips ordinary success notification; a later successful run reconciles derived state.
