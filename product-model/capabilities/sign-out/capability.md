---
{
  "availability": [
    {
      "place": "claudit-web::public"
    },
    {
      "place": "claudit-web::authenticated"
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "backend/login.py#logout"
    }
  ]
}
---

# Sign out

Clear presented access and advance account-wide revocation when available.
