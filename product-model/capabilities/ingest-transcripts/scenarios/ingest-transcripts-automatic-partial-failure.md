---
{
  "kind": "edge",
  "routes": {
    "status": "Status"
  },
  "steps": [
    {
      "text": "Scheduled object failures occur while some work succeeds.",
      "kind": "condition",
      "entities": [],
      "contexts": {
        "status": {
          "place": "claudit-api::status"
        }
      },
      "unattended": true
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
      "contexts": {
        "status": {
          "place": "claudit-api::status"
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
      "contexts": {
        "status": {
          "place": "claudit-api::status"
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
      "contexts": {
        "status": {
          "place": "claudit-api::status"
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
      "contexts": {
        "status": {
          "place": "claudit-api::status"
        }
      }
    },
    {
      "text": "The Product reports failures are reported while successful committed work can receive derived reconciliation.",
      "kind": "product",
      "entities": [],
      "contexts": {
        "status": {
          "place": "claudit-api::status"
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

# Scheduled ingestion partial failure

## Trigger

The Product-owned startup/hourly schedule is due.

## Outcome

Failures are reported while successful committed work can receive derived reconciliation.

## Edge cases

- Per-file committed work is not rolled back as one whole-run transaction.
- A concurrent skip can leave the previous status visible.
- Success notification requires actual changed data and no fatal/abort; it does not refresh every browser consumer.
