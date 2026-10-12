---
{
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/key_layout.py"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/lane_projects.py"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/ingest_persist.py#_persist"
    }
  ],
  "relations": [
    {
      "entity": "coding-session",
      "verb": "groups",
      "cardinality": "one-to-many"
    }
  ]
}
---

# Project

An imported project identity used for grouping and credentialed selection.

## Information kept

- **Identity** — The normalized source-derived project identity after configured identity folding.
- **Display name** — The preserved or recovered project name/path used for display.
- **Activity span** — The earliest and latest source activity retained for the project.
