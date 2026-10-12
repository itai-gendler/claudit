---
{
  "entities": [
    {
      "entity": "coding-session",
      "shows": [
        "Identity",
        "Project",
        "Activity span",
        "Usage summary",
        "Main transcript availability"
      ]
    },
    {
      "entity": "project",
      "shows": [
        "Identity",
        "Display name"
      ]
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "src/sessions-list.jsx#SessionsList"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/api_dashboard.py#_fold_sessions"
    }
  ]
}
---

# Sessions

Selected coding-session summaries with sorting and selection of a session to inspect.
