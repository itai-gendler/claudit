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
      "text": "Transcript/sidecar content or an eligible parser version requires replacement.",
      "kind": "condition",
      "entities": [
        {
          "entity": "transcript",
          "effect": "reads",
          "facts": [
            "Contents"
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
      "text": "The Product updates imported Project, Coding session and Transcript facts.",
      "kind": "product",
      "entities": [
        {
          "entity": "project",
          "effect": "changes",
          "facts": [
            "Identity",
            "Display name",
            "Activity span"
          ]
        },
        {
          "entity": "coding-session",
          "effect": "changes",
          "facts": [
            "Identity",
            "Project",
            "Activity span",
            "Transcript membership",
            "Usage summary",
            "Main transcript availability",
            "Session file scope"
          ]
        },
        {
          "entity": "transcript",
          "effect": "changes",
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
      "text": "The Product removes replaced Request and Tool call occurrences.",
      "kind": "product",
      "entities": [
        {
          "entity": "request",
          "effect": "removes"
        },
        {
          "entity": "tool-call",
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
      "text": "The Product registers the replacement Request and Tool call occurrences.",
      "kind": "product",
      "entities": [
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
          ]
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
      "text": "The Product reports affected parsed facts are replaced atomically per source file.",
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

# Ingestion replacement

## Trigger

Manual reconciliation is initiated.

## Outcome

Affected parsed facts are replaced atomically per source file.

## Edge cases

- Replacement is per-file atomic, not one corpus-wide transaction.
- A fatal or aborted run skips ordinary success notification; a later successful run reconciles derived state.
