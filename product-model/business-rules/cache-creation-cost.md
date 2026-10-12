---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "request",
      "facts": [
        "Billed tokens",
        "TTL creation",
        "Estimated cost",
        "Search count",
        "Meter treatment"
      ]
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/pricing.py#compute_cost"
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
    }
  ]
}
---

# Cache cost preserves TTL quantities and unsplit creation

Let F be fresh input, C total billed creation, E5 explicit five-minute creation, E1 explicit one-hour creation, R reads, O output and S search count. Unsplit creation is max(0,C-E5-E1) and uses the one-hour rate. Cost is [mi*(F*rF + E5*r5 + (E1+unsplit)*r1 + R*rR) + mo*O*rO]/1000000 + S*rS. Omitted write-rate fields can default to fresh-input rates. Claude TTL multipliers are particular rate-card data, not universal provider constants.
