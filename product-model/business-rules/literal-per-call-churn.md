---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "tool-call",
      "facts": [
        "Arguments",
        "Churn",
        "Targets"
      ]
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/parse.py#_tool_churn"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/parse_codex.py#_change_churn"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/bash_churn.py"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/bash_churn_errors.py"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/target_paths.py"
    }
  ]
}
---

# Churn is supported literal per-call estimation

Added/deleted lines derive from Edit/Write, apply_patch and supported literal Bash/ARGV shapes readable without execution. Churn is per-call activity, not net repository change. Unknown or needs-to-run shapes yield no guessed churn. Rejected/failed edits do not claim successful changes; a recognized write can survive a later failing command stage under the implemented settlement policy. Targets are lexical transcript-namespace addresses, not local filesystem inspection.
