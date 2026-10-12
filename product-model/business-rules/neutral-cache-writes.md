---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "request",
      "facts": [
        "Neutral cache writes",
        "Billed tokens"
      ]
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/parse_common.py#resolve_cache_writes"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/parse.py#parse_file"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "src/parser-cache-write.js"
    }
  ]
}
---

# Neutral writes remain separate from billed creation

Provider-neutral writes use explicit creation when present; otherwise subsequent-record read growth is bounded by available fresh input, with no inferred write after the last record. Derivation runs in file order before cross-file canonicalization. This quantity is not a pricing input and no displayed neutral-write total is established.
