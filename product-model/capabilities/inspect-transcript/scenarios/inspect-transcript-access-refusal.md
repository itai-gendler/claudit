---
{
  "kind": "validation",
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
      "text": "Presented credentialed access is missing, invalid, expired or revoked.",
      "kind": "condition",
      "entities": [],
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
      "text": "The Product shows the HTTP 401 loading refusal in Inspector without source content.",
      "kind": "product",
      "entities": [],
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

# Inspector access refusal

## Trigger

A session is selected or the current Inspector context is examined.

## Outcome

Loading is refused without protected transcript disclosure.

## Edge cases

- A main is selected with no defined ordering across multiple eligible mains.
- Detected references are text; no browser sidecar traversal is asserted.
- The estimate uses this main transcript rather than all imported subagent/canonical data.
