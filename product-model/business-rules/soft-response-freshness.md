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
      "id": "read-page-performance",
      "contexts": [
        {
          "place": "claudit-web::authenticated"
        }
      ]
    },
    {
      "type": "capability",
      "id": "retrieve-session-files",
      "contexts": [
        {
          "place": "claudit-api::session-files"
        }
      ]
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/cache.py#_TTLCache"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/cache.py#_IdleLRU"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/ingest_orphans.py"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/ingest_warm.py"
    }
  ]
}
---

# Response freshness is soft and failed refresh can retain stale data

Aggregate cache age marks staleness rather than an unconditional hard eviction. Expired or invalidated entries remain servable during background refresh; refresh failure retains old results. Ingest invalidation is not a one-hour freshness or erasure guarantee. Raw transcript cache is separately source-and-etag keyed with 256 MB capacity and twenty-minute idle eviction; source orphan cleanup explicitly evicts its affected entries.
