---
{
  "kind": "validation",
  "routes": {
    "web": "Sign in"
  },
  "steps": [
    {
      "text": "The User submits an identifier and credential proof.",
      "kind": "actor",
      "entities": [],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "claudit-web::public::sign-in"
        }
      }
    },
    {
      "text": "The submitted identifier is malformed or nonpositive.",
      "kind": "condition",
      "entities": [],
      "contexts": {
        "web": {
          "place": "claudit-web::public::sign-in"
        }
      }
    },
    {
      "text": "The Product returns HTTP 400 displays the identifier rejection without a credential query, password verification or access issuance.",
      "kind": "product",
      "entities": [],
      "actor": "user",
      "contexts": {
        "web": {
          "place": "claudit-web::public::sign-in"
        }
      }
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/login.py#login_post"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/login.py#login_guest"
    }
  ]
}
---

# Invalid account identifier

## Trigger

Entry is submitted from Sign in.

## Outcome

HTTP 400 displays the identifier rejection without a credential query, password verification or access issuance.
