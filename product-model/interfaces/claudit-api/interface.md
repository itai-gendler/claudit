---
{
  "type": "api",
  "actors": [
    "guest",
    "user",
    "web-operator",
    "deployment-operator"
  ],
  "languages": [
    "en"
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/api_sessions.py"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/ingest_progress.py#health"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/app.py#admin_ingest"
    }
  ]
}
---

# API

The documented status, session-file retrieval and maintenance interaction contract.
