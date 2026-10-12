---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "transcript",
      "facts": [
        "Prompt count",
        "Context turns"
      ]
    },
    {
      "type": "entity",
      "id": "request",
      "facts": [
        "Context input",
        "Reply latency",
        "Request metadata"
      ]
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/prompt_gate.py"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/ctx_input.py"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/ctx_turns.py"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/turn_flags.py"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "src/parser.js"
    }
  ]
}
---

# Prompt context and timing boundaries exclude denied harness prompts

A user text opening with an XML tag is harness-injected unless its tag is in the pasted-content keep-list. Denied texts count no ordinary prompt, anchor no reply latency and split no context turn. Eligible context turns use the implemented last-usage/iteration policy and omit implausible/zero turns. Context input can use an iteration peak while billed usage uses its flattened quantities. Pre-request events and prompt-snapshot changes retain their implemented turn attribution.
