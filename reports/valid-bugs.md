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
