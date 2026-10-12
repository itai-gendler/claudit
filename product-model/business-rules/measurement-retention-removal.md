---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "performance-measurement",
      "effect": "removes"
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/ingest_rollup_web_metrics.py"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/web_metrics.py#retention_cutoff"
    }
  ],
  "permits": [
    {
      "actors": [
        "deployment-operator"
      ]
    },
    {
      "unattended": true
    }
  ]
}
---

# Admitted reconciliation removes retained raw measurements

Raw measurements are removed by admitted reconciliation after durable rollup processing, under the Product-owned retention calculation. Manual reconciliation requires its maintenance proof and origin admission; scheduled reconciliation is unattended.
