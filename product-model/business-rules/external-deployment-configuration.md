---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "deployment-settings",
      "effect": "changes",
      "facts": [
        "Transcript sources",
        "Project aliases",
        "Suppressed models",
        "Admin credential configuration",
        "Branding",
        "Privacy link",
        "Rate-limit display"
      ]
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/.env.example"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/branding.py"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/project_aliases.py"
    }
  ],
  "permits": []
}
---

# Deployment configuration is not edited through these Interfaces

Source selection, aliases, suppression, maintenance credential configuration, branding, privacy-link and rate-limit display are configured outside the product Interfaces.
