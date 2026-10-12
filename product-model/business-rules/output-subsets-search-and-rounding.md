---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "request",
      "facts": [
        "Thinking tokens",
        "Search count",
        "Estimated cost"
      ]
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/parse_projection.py#project_records"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/pricing.py#compute_cost"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "src/parser.js#computeSessionStats"
    }
  ]
}
---

# Thinking is a subset search is additive and costs round per request

Thinking/reasoning tokens are already within output and are not charged again. Explicit admissible search count adds the resolved per-search fee; this fee is not multiplied by the context meter. Persisted request cost is rounded to six decimals. Browser main-transcript estimates use the corresponding request-level policy rather than pricing one total at current rates.
