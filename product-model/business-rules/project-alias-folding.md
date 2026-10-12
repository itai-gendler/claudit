---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "project",
      "facts": [
        "Identity",
        "Display name"
      ]
    },
    {
      "type": "entity",
      "id": "deployment-settings",
      "facts": [
        "Project aliases"
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
      "target": "backend/project_aliases.py#resolve"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/project_aliases.py#resolve_chain"
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
  ]
}
---

# Aliases fold project identity in implemented matching order

Externally configured alias matching is case-sensitive SQL LIKE, taking the implemented ordered first match for one-hop folding. Marker identity uses its bounded chain resolution and stored/hash fallback rather than assuming arbitrary recursive aliases. Rekeying changes imported grouping while preserving recovered display names when marker fetch is unavailable.
