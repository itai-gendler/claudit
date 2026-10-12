---
{
  "type": "web",
  "actors": [
    "guest",
    "user",
    "web-operator"
  ],
  "languages": [
    "en"
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "src/app.jsx#App"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/app.py"
    }
  ],
  "entryPoints": [
    {
      "web": "/"
    }
  ]
}
---

# Web dashboard

Browser entry, usage statistics and selected main-transcript inspection.
