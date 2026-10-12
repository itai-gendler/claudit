---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "coding-session",
      "facts": [
        "Transcript membership",
        "Main transcript availability",
        "Usage summary"
      ]
    },
    {
      "type": "capability",
      "id": "browse-sessions",
      "contexts": [
        {
          "place": "claudit-web::authenticated"
        }
      ]
    },
    {
      "type": "capability",
      "id": "inspect-transcript",
      "contexts": [
        {
          "place": "claudit-web::authenticated"
        }
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
      "target": "backend/api_dashboard.py"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/api_sessions.py#get_transcript"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "src/detail-pane.jsx#RefsBlock"
    }
  ]
}
---

# Session browsing is bounded and Inspector retrieves one main

Sessions consumes dashboard summaries rather than the compatibility paginated endpoint. At most 500 upstream summaries are selected, and the browser renders the first 80 after sorting. Aggregate sessions can lack a main transcript. Main retrieval uses LIMIT 1 without defined ordering across eligible mains and does not load every agent file. No upload path or per-file browser dropdown is established. Detected references remain displayed text.
