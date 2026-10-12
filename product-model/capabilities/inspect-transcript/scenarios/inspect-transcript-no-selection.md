---
{
  "kind": "edge",
  "routes": {
    "inspector": "Existing Inspector"
  },
  "steps": [
    {
      "text": "The User opens Inspector without choosing an imported file.",
      "kind": "actor",
      "entities": [],
      "actor": "user",
      "contexts": {
        "inspector": {
          "place": "claudit-web::authenticated::inspector"
        }
      }
    },
    {
      "text": "No imported file is selected or loaded.",
      "kind": "condition",
      "entities": [],
      "contexts": {
        "inspector": {
          "place": "claudit-web::authenticated::inspector"
        }
      }
    },
    {
      "text": "The Product shows No session selected and directs selection from Sessions; it displays no invented content.",
      "kind": "product",
      "entities": [],
      "actor": "user",
      "contexts": {
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

# Inspector no selection

## Trigger

Inspector opens before any imported file is selected.

## Outcome

Inspector offers session selection without fabricated transcript content.
