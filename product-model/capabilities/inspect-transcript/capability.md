---
{
  "availability": [
    {
      "place": "claudit-web::authenticated"
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

# Inspect transcript

Retrieve a selected main transcript and examine its events, tools, browser estimates and context history.
