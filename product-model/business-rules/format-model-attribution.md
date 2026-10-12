---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "transcript",
      "facts": [
        "Models"
      ]
    },
    {
      "type": "entity",
      "id": "request",
      "facts": [
        "Model"
      ]
    },
    {
      "type": "entity",
      "id": "tool-call",
      "facts": [
        "Model"
      ]
    },
    {
      "type": "capability",
      "id": "ingest-transcripts",
      "contexts": [
        {
          "place": "claudit-api::maintenance"
        },
        {
          "place": "claudit-api::status"
        },
        {
          "place": "claudit-web::public"
        },
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
      "target": "backend/parse_lanes.py#refuse_unattributed"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/codex_fork.py"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/parse_codex.py"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/parse_kimi.py"
    }
  ]
}
---

# Model attribution is format-specific and unattributed rows refuse the file

Claude uses recorded message model attribution. Codex keeps first-declared model attribution and fork/replay-prefix policy. Kimi wire model labels and its implemented dated inference remain distinct from rate fallback classification. If a parsed request or tool occurrence lacks a model or has an explicitly refused unknown placeholder, the file is refused. This is distinct from silently skipping malformed JSON lines.
