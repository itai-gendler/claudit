---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "request",
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

# Admitted reconciliation changes request occurrences

Eligible replacement refreshes imported Request usage, timing, metadata and source facts. Derived passes update model attribution, counted status, estimated cost, rate classification and applicable meter treatment from recorded inputs. The Deployment operator grant requires the configured admin credential to be nonempty, the supplied proof to match it by constant-time comparison, and mutating-request origin admission. Browser operator status or a web cookie does not substitute for that proof. The unattended grant is Product-owned startup/hourly execution. Source objects are never changed. Dependent effects declared with `with` inherit the holder operation rather than gaining an independent grant.
