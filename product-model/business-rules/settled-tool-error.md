---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "tool-call",
      "facts": [
        "Result",
        "Settlement",
        "Error outcome",
        "Failure details"
      ]
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/parse.py#_resolve_tool_errors"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/parse_common.py"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/tool_errors.py"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/api.py"
    }
  ]
}
---

# Tool errors use settled results and implemented classification

Tool outcomes are derived from paired results and supported harness-generic failure classification. Error rates use settled-call populations; unavailable results do not fabricate settled failures. Detailed result text and failure classifications remain distinct from publicly granted aggregate error outcomes.
