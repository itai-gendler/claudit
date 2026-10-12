---
{
  "kind": "primary",
  "routes": {
    "status": "Status",
    "guest-overview": "Guest Overview",
    "account-overview": "Account Overview"
  },
  "steps": [
    {
      "text": "Startup or the hourly schedule starts a Product-owned reconciliation.",
      "kind": "condition",
      "entities": [],
      "contexts": {
        "status": {
          "place": "claudit-api::status"
        },
        "guest-overview": {
          "place": "claudit-web::public::overview"
        },
        "account-overview": {
          "place": "claudit-web::authenticated::overview"
        }
      },
      "unattended": true
    },
    {
      "kind": "condition",
      "text": "The complete source listing contains new and changed objects as well as disappeared imported objects.",
      "entities": [],
      "contexts": {
        "status": {
          "place": "claudit-api::status"
        },
        "guest-overview": {
          "place": "claudit-web::public::overview"
        },
        "account-overview": {
          "place": "claudit-web::authenticated::overview"
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
      "contexts": {
        "status": {
          "place": "claudit-api::status"
        },
        "guest-overview": {
          "place": "claudit-web::public::overview"
        },
        "account-overview": {
          "place": "claudit-web::authenticated::overview"
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
      "contexts": {
        "status": {
          "place": "claudit-api::status"
        },
        "guest-overview": {
          "place": "claudit-web::public::overview"
        },
        "account-overview": {
          "place": "claudit-web::authenticated::overview"
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
      "contexts": {
        "status": {
          "place": "claudit-api::status"
        },
        "guest-overview": {
          "place": "claudit-web::public::overview"
        },
        "account-overview": {
          "place": "claudit-web::authenticated::overview"
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
      "contexts": {
        "status": {
          "place": "claudit-api::status"
        },
        "guest-overview": {
          "place": "claudit-web::public::overview"
        },
        "account-overview": {
          "place": "claudit-web::authenticated::overview"
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
      "contexts": {
        "status": {
          "place": "claudit-api::status"
        },
        "guest-overview": {
          "place": "claudit-web::public::overview"
        },
        "account-overview": {
          "place": "claudit-web::authenticated::overview"
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
      "contexts": {
        "status": {
          "place": "claudit-api::status"
        },
        "guest-overview": {
          "place": "claudit-web::public::overview"
        },
        "account-overview": {
          "place": "claudit-web::authenticated::overview"
        }
      }
    },
    {
      "text": "The Product removes suppressed Request and Tool call occurrences from counted storage.",
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
      "contexts": {
        "status": {
          "place": "claudit-api::status"
        },
        "guest-overview": {
          "place": "claudit-web::public::overview"
        },
        "account-overview": {
          "place": "claudit-web::authenticated::overview"
        }
      }
    },
    {
      "text": "The Product reprices stored Request facts.",
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
      "contexts": {
        "status": {
          "place": "claudit-api::status"
        },
        "guest-overview": {
          "place": "claudit-web::public::overview"
        },
        "account-overview": {
          "place": "claudit-web::authenticated::overview"
        }
      }
    },
    {
      "text": "The Product folds configured Project aliases and updates Coding session project grouping before canonical reconciliation.",
      "kind": "product",
      "entities": [
        {
          "entity": "project",
          "effect": "changes",
          "facts": [
            "Identity",
            "Display name"
          ]
        },
        {
          "entity": "coding-session",
          "effect": "changes",
          "facts": [
            "Project"
          ]
        }
      ],
      "contexts": {
        "status": {
          "place": "claudit-api::status"
        },
        "guest-overview": {
          "place": "claudit-web::public::overview"
        },
        "account-overview": {
          "place": "claudit-web::authenticated::overview"
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
        },
        "guest-overview": {
          "place": "claudit-web::public::overview"
        },
        "account-overview": {
          "place": "claudit-web::authenticated::overview"
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
        },
        "guest-overview": {
          "place": "claudit-web::public::overview"
        },
        "account-overview": {
          "place": "claudit-web::authenticated::overview"
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
        },
        "guest-overview": {
          "place": "claudit-web::public::overview"
        },
        "account-overview": {
          "place": "claudit-web::authenticated::overview"
        }
      }
    },
    {
      "text": "The Product processes durable summaries before pruning raw Performance measurement information.",
      "kind": "product",
      "entities": [
        {
          "entity": "performance-measurement",
          "effect": "removes"
        }
      ],
      "contexts": {
        "status": {
          "place": "claudit-api::status"
        },
        "guest-overview": {
          "place": "claudit-web::public::overview"
        },
        "account-overview": {
          "place": "claudit-web::authenticated::overview"
        }
      }
    },
    {
      "text": "The Product reports reconciliation completes; health status and changed-data results become observable.",
      "kind": "product",
      "entities": [],
      "contexts": {
        "status": {
          "place": "claudit-api::status"
        },
        "guest-overview": {
          "place": "claudit-web::public::overview"
        },
        "account-overview": {
          "place": "claudit-web::authenticated::overview"
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
      "target": "backend/ingest.py#_rebuild_derived_state"
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
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/project_aliases.py#rekey_folded_projects"
    }
  ]
}
---

# Startup and hourly ingestion

## Trigger

The Product-owned startup/hourly schedule is due.

## Outcome

Reconciliation completes; health status and changed-data results become observable.

## Edge cases

- Per-file committed work is not rolled back as one whole-run transaction.
- A concurrent skip can leave the previous status visible.
- Success notification requires actual changed data and no fatal/abort; it does not refresh every browser consumer.
