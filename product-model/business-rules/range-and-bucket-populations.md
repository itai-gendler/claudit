---
{
  "appliesTo": [
    {
      "type": "capability",
      "id": "browse-usage",
      "contexts": [
        {
          "place": "claudit-web::public"
        },
        {
          "place": "claudit-web::authenticated"
        }
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
      "id": "export-usage",
      "contexts": [
        {
          "place": "claudit-web::authenticated"
        }
      ]
    },
    {
      "type": "capability",
      "id": "read-page-performance",
      "contexts": [
        {
          "place": "claudit-web::authenticated"
        }
      ]
    },
    {
      "type": "entity",
      "id": "request",
      "facts": [
        "Time",
        "Context input"
      ]
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/api_common.py#_parse_range"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/api_common.py#_bucket_seconds"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/api_ctx_growth.py"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/api.py"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "src/dashboard-binning.js"
    }
  ]
}
---

# Range and bucket selection retain actual query populations

Request timestamps, hourly rollups and file-modification-selected context traces have different range semantics. Display binning is never finer than the server bucket. Aggregate context traces can include all turns of selected files; main ending-context selection and main retrieval use their separate policies. Activity uses Europe/Prague including timezone transitions; provider schedules use UTC. Invalid or overflowing range arithmetic is rejected rather than becoming an internal failure.
