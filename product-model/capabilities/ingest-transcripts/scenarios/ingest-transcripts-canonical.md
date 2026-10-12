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
      "text": "Duplicate/replayed occurrences or agent attribution require reconciliation.",
      "kind": "condition",
      "entities": [],
      "contexts": {
        "maintenance": {
          "place": "claudit-api::maintenance"
        }
      }
    },
    {
      "text": "The Product selects canonical Request and Tool call occurrences, adopts eligible original models into losing replayed copies, and extends Transcript model attribution.",
      "kind": "product",
      "entities": [
        {
          "entity": "request",
          "effect": "changes",
          "facts": [
            "Counted status",
            "Model"
          ]
        },
        {
          "entity": "tool-call",
          "effect": "changes",
          "facts": [
            "Counted status",
            "Model"
          ]
        },
        {
          "entity": "transcript",
          "effect": "changes",
          "facts": [
            "Models"
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
      "text": "The Product resolves named teammate Transcript agent attribution from the latest eligible successful canonical dispatch preceding its activity.",
      "kind": "product",
      "entities": [
        {
          "entity": "transcript",
          "effect": "changes",
          "facts": [
            "Agent attribution"
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
      "text": "The Product rebuilds Coding session usage and activity summaries from the reconciled counted population.",
      "kind": "product",
      "entities": [
        {
          "entity": "coding-session",
          "effect": "changes",
          "facts": [
            "Usage summary"
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
      "text": "The Product reports canonical selection, adopted models and teammate roles determine the rebuilt counted population.",
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
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/ingest_rollup_state.py#adopt_original_models"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/ingest_rollup_state.py#resolve_teammate_agent_types"
    }
  ]
}
---

# Ingestion canonical

## Trigger

Manual reconciliation is initiated.

## Outcome

Canonical selection, adopted models and teammate roles determine the rebuilt counted population.

## Edge cases

- Replacement is per-file atomic, not one corpus-wide transaction.
- A fatal or aborted run skips ordinary success notification; a later successful run reconciles derived state.
