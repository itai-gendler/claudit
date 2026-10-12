---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "performance-measurement"
    },
    {
      "type": "capability",
      "id": "record-page-performance",
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
      "target": "backend/web_metrics.py"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/ingest_rollup_web_metrics.py"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/api_web_metrics.py#web_metrics_readout"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "src/perf-panel.jsx#WebMetricsPanel"
    }
  ]
}
---

# Performance admission retention and approximation differ

Batches contain at most fifty measurements and use closed category/part/region/phase vocabularies; supported finite numeric values are clamped. Admission checks existing retained counts before insertion: 20000 per non-guest user ID and 2000 for the shared guest ID. Batches can overshoot these thresholds and guest browsers do not have separate quotas. The raw working set is 54 hours, computed as twice the widest latency bucket plus six hours; pruning occurs through durable rollup processing, not an independent deletion deadline. Only complete closed buckets are retained as durable summaries, with raw tail unioned for wider ranges. Ranges fitting raw retention have exact percentiles; wider rollup/tail percentile blends are approximate and report their actual population. Layout shift and blocking summaries are sums across visits, not one whole-range cumulative score. There is no project grain.
