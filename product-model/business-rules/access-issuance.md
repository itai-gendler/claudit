---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "web-session",
      "effect": "creates",
      "contexts": [
        {
          "place": "claudit-web::public::sign-in"
        }
      ]
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
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/session.py#check_origin"
    }
  ],
  "permits": [
    {
      "actors": [
        "guest"
      ],
      "when": [
        {
          "fact": "Audience",
          "is": "Guest"
        }
      ]
    },
    {
      "actors": [
        "user",
        "web-operator"
      ],
      "when": [
        {
          "fact": "Audience",
          "is": "Account"
        }
      ]
    }
  ]
}
---

# Access is issued through admitted entry

Guest entry creates Guest-audience access. Account entry creates Account-audience access only after accepted current credential proof, fresh credential reread, and bounded login admission. Both mutating entries require matching-origin evidence.
