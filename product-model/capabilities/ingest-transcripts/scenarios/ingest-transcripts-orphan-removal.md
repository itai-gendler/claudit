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
      "text": "Complete source listing establishes that the last files of a project/session disappeared.",
      "kind": "condition",
      "entities": [
        {
          "entity": "project",
          "effect": "reads",
          "facts": [
            "Identity"
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
      "text": "The Product removes the missing Transcript and its dependent Request and Tool call occurrences, then evicts raw cached bytes.",
      "kind": "product",
      "entities": [
        {
          "entity": "transcript",
          "effect": "removes"
        },
        {
          "entity": "request",
          "effect": "removes",
          "with": "transcript"
        },
        {
          "entity": "tool-call",
          "effect": "removes",
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
      "text": "The Product removes the unreferenced Project and Coding session grouping.",
      "kind": "product",
      "entities": [
        {
          "entity": "project",
          "effect": "removes"
        },
        {
          "entity": "coding-session",
          "effect": "removes",
          "with": "project"
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
      "text": "The Product reports imported missing-source facts and unreferenced grouping are removed and raw cached bytes evicted.",
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

# Ingestion orphan removal

## Trigger

Manual reconciliation is initiated.

## Outcome

Imported missing-source facts and unreferenced grouping are removed and raw cached bytes evicted.

## Edge cases

- Replacement is per-file atomic, not one corpus-wide transaction.
- A fatal or aborted run skips ordinary success notification; a later successful run reconciles derived state.
