---
{
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/api_dashboard.py#_fold_sessions"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/api_sessions.py#get_transcript"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/api_sessions.py#get_sidecar"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/key_layout.py#classify"
    }
  ],
  "relations": [
    {
      "entity": "transcript",
      "verb": "contains",
      "cardinality": "one-to-many"
    }
  ]
}
---

# Coding session

An independently addressed session grouping whose usage can include multiple transcript files.

## Information kept

- **Identity** — The source session identifier used to select the session.
- **Project** — Its imported project grouping.
- **Activity span** — The selected population earliest and latest activity.
- **Transcript membership** — The associated main and agent transcript occurrences.
- **Usage summary** — Selected requests, models, billed tokens, cost and numeric context summary across counted occurrences.
- **Main transcript availability** — Whether a main transcript exists for retrieval.
- **Session file scope** — The source prefix established from a selected main transcript for session-relative retrieval.
