---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "request",
      "facts": [
        "Meter treatment",
        "Billed tokens",
        "Estimated cost"
      ]
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/pricing.py#meter_flag"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/pricing.py#long_context_threshold"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/parse_projection.py#project_records"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/parse_codex.py#_codex_token_count"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/parse_common.py"
    }
  ]
}
---

# Applicable context metering charges the whole request

Threshold comparison is strict: above the applicable threshold the whole billed request partition receives the input/output factors, not just the excess. Claude parsing consults model meter membership. Codex applies its per-model/default threshold test without that membership check. Kimi parsing does not supply the same adjustment. Thresholds and optional factors are pricing data; provider does not change the meter decision.
