---
{
  "id": "claudit",
  "summary": "Self-hosted statistics and transcript inspection for Claude Code, Codex and Kimi coding sessions.",
  "category": "developer-tools",
  "authors": [
    {
      "name": "Nitjsefnie"
    }
  ],
  "license": "MIT",
  "languages": [
    "en"
  ],
  "limitations": [
    "Credentials and operator entitlement are managed externally.",
    "Transcripts arrive through configured object storage or its local mirror; source objects remain externally managed.",
    "Credentialed readers share the deployment corpus; access is not divided by account ownership of projects or sessions.",
    "The application has no local upload, transcript editor, transcript deletion control or self-service erasure.",
    "The product presents statistics and transcripts without quality scoring, coaching or AI narrative.",
    "Costs are estimates from recorded usage and shipped rate data, without a guarantee of invoice or subscription-charge accuracy.",
    "Browser execution requires externally loaded React, ReactDOM and Babel; there is no bundled fallback."
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/app.py"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/session.py"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/r2.py"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "src/app.jsx#App"
    },
    {
      "kind": "doc",
      "role": "context",
      "target": "README.md"
    },
    {
      "kind": "doc",
      "role": "context",
      "target": "PRIVACY.md"
    },
    {
      "kind": "doc",
      "role": "context",
      "target": "LICENSE"
    }
  ]
}
---

# claudit — Claude Code Usage Dashboard

claudit presents quantitative usage and retrieved coding-session transcripts. Readers examine tokens, cache behavior, estimated cost, tools, timing, context and activity across the deployment corpus, then inspect a retrieved main transcript. Deployment operators reconcile externally supplied transcripts; web operators examine page-performance observations.
