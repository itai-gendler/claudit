---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "tool-call",
      "effect": "changes"
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/ingest.py#run_ingest"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/ingest_persist.py#_persist"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/ingest_orphans.py"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/ingest_rollup_state.py"
    }
  ],
  "permits": [
    {
      "actors": [
        "deployment-operator"
      ]
    },
    {
      "unattended": true
    }
  ]
}
---

# Admitted reconciliation changes tool occurrences

Eligible replacement refreshes imported Tool call invocation, result, timing, settlement, error, churn, dispatch and lexical-target facts. Canonical reconciliation updates counted status and eligible replay model attribution. The Deployment operator grant requires the configured admin credential to be nonempty, the supplied proof to match it by constant-time comparison, and mutating-request origin admission. Browser operator status or a web cookie does not substitute for that proof. The unattended grant is Product-owned startup/hourly execution. Source objects are never changed. Dependent effects declared with `with` inherit the holder operation rather than gaining an independent grant.
