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
      "text": "The identifier has no credential record, the stored password is absent, verification fails, or the credential changes during verification.",
      "kind": "condition",
      "entities": [],
      "contexts": {
        "web": {
          "place": "claudit-web::public::sign-in"
        }
      }
    },
    {
      "text": "The Product returns HTTP 401 displays the same generic credential rejection for absent records, missing/wrong passwords or changed credentials; no access is bound.",
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

# Generic credential rejection

## Trigger

Entry is submitted from Sign in.

## Outcome

HTTP 401 displays the same generic credential rejection for absent records, missing/wrong passwords or changed credentials; no access is bound.

## Edge cases

- Unknown, missing-password and wrong-password failures share the generic response and normalized verification work.
