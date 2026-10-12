---
{
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/parse.py#parse_file"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/key_layout.py#classify"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/agent_sidecar.py#apply_agent_sidecar"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/api_sessions.py#get_transcript"
    }
  ],
  "relations": [
    {
      "entity": "request",
      "verb": "contains",
      "cardinality": "one-to-many"
    },
    {
      "entity": "tool-call",
      "verb": "contains",
      "cardinality": "one-to-many"
    }
  ]
}
---

# Transcript

A source-addressed coding-session transcript, including main and agent files under one common fact family.

## Information kept

- **Object path** — The configured bucket-qualified source address; public displays can omit the bucket qualification.
- **Session** — The coding-session grouping selected by source layout.
- **Main designation** — Whether the file is classified as a main transcript.
- **Models** — Recorded or inferred model attribution under the format-specific policy.
- **Agent attribution** — Recorded/default role and available teammate attribution.
- **Prompt count** — Ordinary user prompts admitted by the prompt gate.
- **Context turns** — Recorded prompt/context history under the parser policy.
- **Rate-limit hits** — Recorded rate-limit observations.
- **Contents** — The source transcript bytes and their parsed events.
