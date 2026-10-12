---
{
  "access": "public",
  "actors": [
    "guest",
    "user",
    "web-operator",
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
      "claudit-api": "/health"
    }
  ]
}
---

# Public status

People read database availability, current reconciliation progress and public last-run metadata.
