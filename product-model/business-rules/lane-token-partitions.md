---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "request",
      "facts": [
        "Billed tokens",
        "TTL creation",
        "Thinking tokens"
      ]
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/parse_projection_usage.py#_usage_tokens"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/parse_codex.py#_codex_token_count"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/parse_common.py"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/parse_lanes.py#to_claudit"
    }
  ]
}
---

# Billing retains lane-specific subset and cumulative semantics

Claude fresh input, creation, reads and output remain distinct billed categories. Codex cumulative usage is differenced; repeated/nonadvancing snapshots do not create extra usage except the supported search case. Cached input and write input are subsets removed from total input to derive fresh input. Reasoning is an output subset. Kimi lane adaptation preserves its available usage and leaves unavailable TTL-split quantities zero rather than inventing them.
