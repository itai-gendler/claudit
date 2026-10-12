---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "performance-measurement",
      "effect": "creates"
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/api_web_metrics.py#post_metrics"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/api_web_metrics.py#_write"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/web_metrics.py#parse_batch"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/session.py#check_origin"
    }
  ],
  "permits": [
    {
      "unattended": true
    }
  ]
}
---

# Admitted automatic observations create measurements

Automatic collection requires a valid presented account or guest session and matching-origin evidence. Only a fully validated batch is stored after the existing retained-population admission check. Invalid proof, JSON, vocabulary, shape or pre-batch count refusal prevents creation.
