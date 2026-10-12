---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "request",
      "facts": [
        "Estimated cost",
        "Billed tokens",
        "TTL creation",
        "Meter treatment"
      ],
      "contexts": [
        {
          "place": "claudit-web::public::cache"
        },
        {
          "place": "claudit-web::authenticated::cache"
        }
      ]
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/api_cache.py#_cache_queries"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/api_common.py#_accumulate_row_buckets"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/api_cache.py#_session_total"
    }
  ]
}
---

# Stored Cache total and reconstructed components differ in evidence

Cache totals sum persisted request costs. Component folding retains model/provider, rate epoch, context flag and stored factor pair, including unsplit creation and search. Scheduled token decomposition can be rescaled toward stored token cost; banded components retain approximation. Derived components and displayed rounding do not replace the stored total or guarantee an exact allocation to each category.
