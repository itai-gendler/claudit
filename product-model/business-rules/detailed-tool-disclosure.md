---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "tool-call",
      "effect": "reads",
      "facts": [
        "Arguments",
        "Result",
        "Failure details",
        "Dispatch attribution",
        "Targets"
      ],
      "contexts": [
        {
          "place": "claudit-web::authenticated::inspector"
        }
      ]
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "src/detail-pane.jsx#ToolCallDetail"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "src/detail-pane.jsx#ToolResultDetail"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/session.py#_guest_denied"
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

# Tool contents and detailed attribution are credentialed

Every selected disclosure requires valid presented access. Account access must resolve the current credential binding and account revocation; guest access must pass its process-bound signature and age checks. No project/session ownership filter is applied to account readers. The selected main transcript supplies detailed arguments/results, failure details, dispatch information and lexical targets in Inspector.
