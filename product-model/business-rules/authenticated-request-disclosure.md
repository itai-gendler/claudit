---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "request",
      "effect": "reads",
      "contexts": [
        {
          "place": "claudit-web::authenticated"
        }
      ]
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/session.py#_session_denied"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/session.py#_guest_denied"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/api_export.py"
    }
  ],
  "permits": [
    {
      "actors": [
        "user",
        "web-operator"
      ]
    }
  ]
}
---

# Authenticated usage reads require account access

Every selected disclosure requires valid presented access. Account access must resolve the current credential binding and account revocation; guest access must pass its process-bound signature and age checks. No project/session ownership filter is applied to account readers. This grant covers authenticated browsing, inspection and export; a public numeric-read grant does not admit guest PNG export or credentialed places.
