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
      "text": "A failure window or bounded history/in-flight admission refuses the attempt.",
      "kind": "condition",
      "entities": [],
      "contexts": {
        "web": {
          "place": "claudit-web::public::sign-in"
        }
      }
    },
    {
      "text": "The Product returns HTTP 429 displays login admission refusal before access issuance.",
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

# Login admission exhausted

## Trigger

Entry is submitted from Sign in.

## Outcome

HTTP 429 displays login admission refusal before access issuance.
