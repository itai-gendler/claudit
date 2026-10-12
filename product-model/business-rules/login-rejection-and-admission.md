---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "web-session",
      "effect": "creates"
    },
    {
      "type": "entity",
      "id": "account",
      "effect": "changes",
      "facts": [
        "Credential binding"
      ]
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/login.py"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/login_workers.py"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/auth.py"
    }
  ]
}
---

# Credential rejection is generic and admission bounded

Malformed/nonpositive identifiers have their own rejection. Unknown account, absent password, wrong password and stale proof after a credential change share generic rejection. Failure verification work is normalized toward the write work factor; hashes above that target can take longer. Admission limits five failures per IP-plus-user and twenty per IP in five minutes. History and in-flight maps are bounded at 4096 keys, prune expired entries and refuse unseen keys rather than evicting live windows. Worker admission is retained until verification work completes.
