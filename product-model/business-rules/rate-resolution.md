---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "request",
      "facts": [
        "Model",
        "Provider",
        "Time",
        "Estimated cost",
        "Rate classification"
      ]
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/pricing.py#resolve"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/pricing_load.py"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "src/rates.js"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "src/pricing.json"
    }
  ]
}
---

# Rate resolution follows its implemented precedence

Free and stealth identifier shapes resolve to zero before ordinary matching. Normalized applicable provider rows precede exact model rows, tracked bare-vendor histories, family fallback and default fallback. Provider normalization and bounded snapshot/variant handling do not establish arbitrary model aliases. Family/default results are rate estimates; a format-inferred model is a separate attribution fact. Running product rates come from the shipped pricing document, not a live vendor lookup.
