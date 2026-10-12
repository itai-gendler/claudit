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
      "text": "Configured sources are listed completely and new supported files are parsed.",
      "kind": "condition",
      "entities": [],
      "contexts": {
        "maintenance": {
          "place": "claudit-api::maintenance"
        }
      }
    },
    {
      "text": "The Product registers Project and Coding session identity with the new Transcript, Request and Tool call occurrences.",
      "kind": "product",
      "entities": [
        {
          "entity": "project",
          "effect": "creates",
          "facts": [
            "Identity",
            "Display name",
            "Activity span"
          ]
        },
        {
          "entity": "coding-session",
          "effect": "creates",
          "facts": [
            "Identity",
            "Project",
            "Activity span",
            "Transcript membership",
            "Usage summary",
            "Main transcript availability",
            "Session file scope"
          ],
          "with": "project"
        },
        {
          "entity": "transcript",
          "effect": "creates",
          "facts": [
            "Object path",
            "Session",
            "Main designation",
            "Models",
            "Agent attribution",
            "Prompt count",
            "Context turns",
            "Rate-limit hits",
            "Contents"
          ],
          "with": "coding-session"
        },
        {
          "entity": "request",
          "effect": "creates",
          "facts": [
            "Identity",
            "Time",
            "Model",
            "Provider",
            "Billed tokens",
            "TTL creation",
            "Thinking tokens",
            "Neutral cache writes",
            "Search count",
            "Estimated cost",
            "Rate classification",
            "Meter treatment",
            "Context input",
            "Visible reply size",
            "Reply latency",
            "Request metadata",
            "Counted status",
            "Source line",
            "Source location"
          ],
          "with": "transcript"
        },
        {
          "entity": "tool-call",
          "effect": "creates",
          "facts": [
            "Identity",
            "Time",
            "Name",
            "Model",
            "Arguments",
            "Result",
            "Settlement",
            "Error outcome",
            "Failure details",
            "Churn",
            "Dispatch attribution",
            "Targets",
            "Counted status"
          ],
          "with": "transcript"
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
            "Usage summary",
            "Activity span",
            "Main transcript availability"
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
      "text": "The Product reports the initiated reconciliation completes and returns its changed-data summary.",
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

# Ingestion manual

## Trigger

Manual reconciliation is initiated.

## Outcome

The initiated reconciliation completes and returns its changed-data summary.

## Edge cases

- Replacement is per-file atomic, not one corpus-wide transaction.
- A fatal or aborted run skips ordinary success notification; a later successful run reconciles derived state.
- Derived phases run in suppression, repricing, aliases, canonical flags, teammate attribution and rollup order.
- Suppression can independently remove Request and Tool call rows while retaining source Transcript information.
