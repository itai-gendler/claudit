---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "request",
      "effect": "reads",
      "facts": [
        "Source location"
      ],
      "contexts": [
        {
          "place": "claudit-web::public"
        },
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
      "target": "backend/api_cache.py#cache_view_route"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/api.py"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "src/detail-pane.jsx"
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

# Request source locations are credentialed

Every selected disclosure requires valid presented access. Account access must resolve the current credential binding and account revocation; guest access must pass its process-bound signature and age checks. No project/session ownership filter is applied to account readers. Source addresses used for detailed identification are credentialed disclosure. Numeric source line numbers are a separate fact and remain in guest Cache rows; stripping the address does not strip the line.
