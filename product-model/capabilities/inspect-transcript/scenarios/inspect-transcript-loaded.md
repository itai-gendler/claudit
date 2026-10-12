---
{
  "kind": "primary",
  "routes": {
    "sessions": "From Sessions",
    "inspector": "Existing Inspector"
  },
  "steps": [
    {
      "text": "The User selects a session to inspect.",
      "kind": "actor",
      "entities": [],
      "actor": "user",
      "contexts": {
        "sessions": {
          "place": "claudit-web::authenticated::sessions"
        },
        "inspector": {
          "place": "claudit-web::authenticated::inspector"
        }
      }
    },
    {
      "text": "The Coding session has a retrievable main file.",
      "kind": "condition",
      "entities": [
        {
          "entity": "coding-session",
          "effect": "reads",
          "facts": [
            "Main transcript availability"
          ]
        }
      ],
      "contexts": {
        "sessions": {
          "place": "claudit-web::authenticated::sessions"
        },
        "inspector": {
          "place": "claudit-web::authenticated::inspector"
        }
      },
      "actor": "user"
    },
    {
      "text": "The Product retrieves Transcript contents and opens Inspector.",
      "kind": "product",
      "entities": [
        {
          "entity": "coding-session",
          "effect": "reads",
          "facts": [
            "Identity",
            "Main transcript availability"
          ]
        },
        {
          "entity": "transcript",
          "effect": "reads",
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
      "actor": "user",
      "contexts": {
        "sessions": {
          "place": "claudit-web::authenticated::inspector"
        },
        "inspector": {
          "place": "claudit-web::authenticated::inspector"
        }
      }
    },
    {
      "text": "The User examines Transcript events, Request estimates and Tool call details, then context history.",
      "kind": "actor",
      "entities": [
        {
          "entity": "transcript",
          "effect": "reads",
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
        },
        {
          "entity": "request",
          "effect": "reads",
          "facts": [
            "Identity",
            "Time",
            "Model",
            "Provider",
            "Billed tokens",
            "TTL creation",
            "Thinking tokens",
            "Search count",
            "Estimated cost",
            "Rate classification",
            "Meter treatment",
            "Context input",
            "Visible reply size",
            "Reply latency",
            "Counted status",
            "Request metadata",
            "Source location",
            "Source line"
          ]
        },
        {
          "entity": "tool-call",
          "effect": "reads",
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
      "actor": "user",
      "contexts": {
        "sessions": {
          "place": "claudit-web::authenticated::inspector"
        },
        "inspector": {
          "place": "claudit-web::authenticated::inspector"
        }
      }
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "src/app.jsx#makeTranscriptLoader"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "src/detail-pane.jsx#EventDetail"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "src/context-growth-view.jsx#ContextGrowthView"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/api_sessions.py#get_transcript"
    }
  ]
}
---

# Inspector loaded

## Trigger

A session is selected or the current Inspector context is examined.

## Outcome

Inspector presents the selected main transcript, event/tool details, browser estimates and context history.

## Edge cases

- A main is selected with no defined ordering across multiple eligible mains.
- Detected references are text; no browser sidecar traversal is asserted.
- The estimate uses this main transcript rather than all imported subagent/canonical data.
