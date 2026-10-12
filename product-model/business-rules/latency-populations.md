---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "request",
      "facts": [
        "Reply latency",
        "Time",
        "Counted status"
      ]
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/api.py#reply_latency"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/ingest_rollup_latency.py"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/constants.py#LATENCY_BUCKETS"
    }
  ]
}
---

# Latency percentiles describe selected populations

Latency uses eligible admitted-prompt anchors and the selected counted-request population. Percentiles are computed at the display width; project-filtered percentiles cannot be pooled into all-project percentiles. Stored all-project rows and each configured width retain separate populations. Extreme one-percent observations are shown only when the supported sample threshold is met.
