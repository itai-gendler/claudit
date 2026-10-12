---
{
  "entities": [
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
        "Source location"
      ]
    },
    {
      "entity": "tool-call",
      "shows": [
        "Name",
        "Model",
        "Settlement",
        "Error outcome",
        "Churn",
        "Counted status"
      ]
    },
    {
      "entity": "transcript",
      "shows": [
        "Models",
        "Agent attribution",
        "Prompt count",
        "Context turns",
        "Rate-limit hits",
        "Main designation"
      ]
    },
    {
      "entity": "coding-session",
      "shows": [
        "Identity",
        "Activity span",
        "Usage summary",
        "Main transcript availability"
      ]
    },
    {
      "entity": "project",
      "shows": [
        "Identity",
        "Display name",
        "Activity span"
      ]
    },
    {
      "entity": "performance-measurement",
      "shows": [
        "Time",
        "Category",
        "Part",
        "Region",
        "Phase",
        "Value",
        "Source audience"
      ]
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "src/app.jsx#Dashboard"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/api_dashboard.py#dashboard_route"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "src/perf-panel.jsx#WebMetricsPanel"
    }
  ]
}
---

# Overview

The selected usage population, token/cost distributions, tools, activity and context observations. Page performance appears for its classified operator audience.
