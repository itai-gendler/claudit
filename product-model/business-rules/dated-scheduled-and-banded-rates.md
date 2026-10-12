---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "request",
      "facts": [
        "Time",
        "Provider",
        "Estimated cost",
        "Rate classification"
      ]
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/pricing.py#_in_window"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/pricing.py#_scheduled"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/pricing.py#_provider_rates"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/rate_boundaries.py"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/api_common.py#_row_is_banded"
    }
  ]
}
---

# Historical cutovers starts schedules and bands differ

Request time selects historical windows with end-exclusive cutovers. A provider row before its applicable start falls back rather than borrowing a future provider history. Applicable recurring schedules use their UTC weekday/time policy and ordered matching windows. Bare-vendor resolution does not automatically inherit a host schedule. Banded rates are time-weighted means for their recorded interval, not an asserted listed price. Missing timestamps use the implemented list/latest resolution.
