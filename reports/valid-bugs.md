# Validated findings (running count 0)

- 6 lead(s) marked VALID at 2026-09-10 06:43:39 UTC
  - **Verdict: VALID**
  - **Verdict: VALID** (low severity, but information disclosure of internal architecture)
  - **Verdict: VALID** (low severity)
  - | 1 | Anonymous GraphQL introspection via WS (full schema + PII fields) | **VALID** | 5.3 |
  - | 3 | Subscription error disclosure (kycUpdated/polymarketOrders) | **VALID** | 3.1 |
  - | 4 | Anonymous Socket.IO real-time broadcast feed | **VALID** | 3.1 |

- 2 lead(s) marked VALID at 2026-09-11 13:24:31 UTC
  - **Verdict: VALID**
  - | 1 | GraphQL anonymous introspection (full schema + PII/financial field disclosure) | **VALID** | 5.3 |

- 3 lead(s) marked VALID at 2026-09-11 17:14:32 UTC
  - | Q4 Provable | **No** | Needs a valid user session (`connect.sid`) to test; cannot verify without signing up. Auth is server-side. |
  - | Q4 Provable | **No** | Needs valid session to test parameter influence |
  - | Q4 Provable | **No** | Needs valid session + correct body format |

- 5 lead(s) marked VALID at 2026-09-12 21:20:20 UTC
  - **VERDICT: VALID**
  - **VERDICT: VALID**
  - | Q4 Provable | PARTIAL | 401 baseline confirmed passively; requires valid session to prove/disprove escalation (AUTH_HELPED) |
  - | 1 | GraphQL Anonymous Introspection | **VALID** | 7.5 | Report via bugs.olivermaicher.eu |
  - | 2 | GraphQL Pre-Auth Mutation Execution | **VALID** | 5.3 | Report via bugs.olivermaicher.eu |

- 7 lead(s) marked VALID at 2026-09-17 19:56:11 UTC
  - | Q4 Provable | PARTIALLY — 401 baseline confirmed without auth; requires valid session cookie (connect.sid) to test if standard user grants admin access. Cannot prove non-invasively without a test ac
  - **Verdict: HOLD** — Promising lead (admin routes on non-Cloudflare-gated surface). Needs browser-phase verification with a valid Roobet session to test if standard user auth grants admin access. Canno
  - | Q4 Provable | PARTIALLY — parameter acceptance confirmed (401 not 404); needs valid session to test IDOR |
  - **Verdict: HOLD** — IDOR candidate. Needs browser-phase with valid session + two test accounts to confirm cross-user data access.
  - | Q4 Provable | NO — requires valid session + exact POST body; cannot test without auth |
  - | Q7 Reasonable triager | NO — no proof of bypass; endpoints require valid session |
  - **Verdict: HOLD** — Needs browser-phase with valid session. Cannot validate passively.
