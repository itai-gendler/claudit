---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "request",
      "facts": [
        "Identity",
        "Counted status",
        "Model"
      ]
    },
    {
      "type": "entity",
      "id": "tool-call",
      "facts": [
        "Identity",
        "Counted status",
        "Model"
      ]
    },
    {
      "type": "entity",
      "id": "transcript",
      "facts": [
        "Models",
        "Agent attribution"
      ]
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/ingest_rollup_state.py#recompute_canonical"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/ingest_rollup_state.py#adopt_original_models"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "src/record-dedup.js"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/ingest_rollup_state.py#resolve_teammate_agent_types"
    }
  ]
}
---

# Counted identity follows canonical duplicate and replay selection

Global request identity comparison prefers original over replayed occurrences, attributed over unattributed copies, then the implemented file/line ordering. Null identity occurrences remain counted independently. Tool identity has the corresponding canonical policy. Losing replayed Request and Tool call copies with a canonical original adopt that original’s non-null Model; transcript Models are extended accordingly. Named teammate Transcript Agent attribution is then resolved from an eligible preceding successful canonical dispatch before rollups. Source occurrence membership does not imply exclusive logical identity ownership. Aggregate reads use canonical flags; browser main-transcript and PNG populations are separately constrained.
