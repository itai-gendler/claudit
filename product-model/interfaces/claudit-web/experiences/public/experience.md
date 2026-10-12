---
{
  "access": "public",
  "actors": [
    "guest",
    "user",
    "web-operator"
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
      "claudit-web": "/login"
    }
  ]
}
---

# Public access

People establish access and use the guest dashboard without an authenticated account.
