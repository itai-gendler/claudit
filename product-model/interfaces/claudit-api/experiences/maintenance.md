---
{
  "access": "restricted",
  "actors": [
    "deployment-operator"
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/session.py#auth_middleware"
    }
  ],
  "entryPoints": [
    {
      "claudit-api": "/admin/ingest"
    }
  ]
}
---

# Maintenance

Deployment operators initiate reconciliation of configured transcript sources.
