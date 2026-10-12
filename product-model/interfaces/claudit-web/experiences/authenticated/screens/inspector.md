---
{
  "entities": [
    {
      "entity": "transcript",
      "shows": [
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
      "shows": [
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
      "shows": [
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
    },
    {
      "entity": "coding-session",
      "shows": [
        "Identity",
        "Main transcript availability"
      ]
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "src/app.jsx#SessionView"
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
    }
  ]
}
---

# Inspector

The fetched main transcript with event selection, message/tool contents, detected reference text, session estimates and context history.
