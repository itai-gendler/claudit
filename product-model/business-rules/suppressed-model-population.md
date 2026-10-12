---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "request"
    },
    {
      "type": "entity",
      "id": "tool-call"
    },
    {
      "type": "entity",
      "id": "deployment-settings",
      "facts": [
        "Suppressed models"
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
      "target": "backend/ingest_rollup_state.py#purge_suppressed"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/ingest_scope.py"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "src/parser.js#computeSessionStats"
    }
  ]
}
---

# Suppression changes counted corpus without deleting source objects

Configured model patterns apply the implemented case-insensitive matching to imported request/tool rows. Suppression can remove these rows and force derived population rebuild while retaining transcript file/context information and source objects. Browser raw-main estimation is not silently equated to this suppressed aggregate population.
