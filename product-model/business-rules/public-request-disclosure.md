---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "request",
      "effect": "reads",
      "facts": [
        "Identity",
        "Time",
        "Model",
        "Provider",
        "Billed tokens",
        "TTL creation",
        "Thinking tokens",
        "Search count",
        "Estimated cost",
        "Rate classification",
        "Meter treatment",
        "Context input",
        "Visible reply size",
        "Reply latency",
        "Counted status",
        "Source line"
      ],
      "contexts": [
        {
          "place": "claudit-web::public::overview"
        },
        {
          "place": "claudit-web::public::cache"
        }
      ]
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/session.py#_guest_denied"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/api_cache.py#cache_view_route"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/api.py#reply_latency_route"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/api_ctx_growth.py#context_growth_session"
    }
  ],
  "permits": [
    {
      "actors": [
        "guest"
      ]
    }
  ]
}
---

# Public browsing receives guest-safe request statistics

Valid guest access admits the selected numeric usage facts. Request metadata and source addresses are excluded. Numeric source line numbers remain in top-request rows. Nonempty project filtering is refused; top-request/context/latency source paths are stripped before public disclosure.
