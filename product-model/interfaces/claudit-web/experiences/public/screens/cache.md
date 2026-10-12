---
{
  "entities": [
    {
      "entity": "request",
      "shows": [
        "Identity",
        "Time",
        "Model",
        "Provider",
        "Billed tokens",
        "TTL creation",
        "Search count",
        "Estimated cost",
        "Rate classification",
        "Meter treatment",
        "Context input",
        "Source line"
      ]
    },
    {
      "entity": "transcript",
      "shows": [
        "Models",
        "Context turns"
      ]
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "src/views/cache-view.jsx"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "src/views/context-growth-view-v2.jsx"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/api_cache.py#cache_view_route"
    }
  ]
}
---

# Cache

Prompt-cache quantities, hit percentage, TTL cost components, top requests and context-growth distributions for the selected population. Top requests retain numeric source lines; source paths are not presented by this view.
