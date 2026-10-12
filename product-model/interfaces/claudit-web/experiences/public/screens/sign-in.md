---
{
  "entities": [
    {
      "entity": "account",
      "collects": [
        "User identifier",
        "Web credentials"
      ]
    },
    {
      "entity": "deployment-settings",
      "shows": [
        "Branding",
        "Privacy link"
      ]
    }
  ],
  "entryPoints": [
    {
      "claudit-web": "/login"
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/login_page.py"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/login.py#login_post"
    }
  ]
}
---

# Sign in

The place for supplying account credential proof or choosing guest entry. Entry outcomes remain here until access is established.
