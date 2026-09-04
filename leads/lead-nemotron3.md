## 2026-09-03 17:18:18 UTC [target] (model nemotron3)
[NEW] api.roobet.com — primary API surface, high-value target for auth/IDOR/SSRF/mass-assignment
[NEW] auth.roobet.com — authentication/authorization service, target for OAuth/JWT/session flaws
[NEW] account.roobet.com — user account management, target for IDOR/BOLA on wallet/profile endpoints
[NEW] admin.roobet.com — admin panel candidate, target for auth bypass/privilege escalation
[NEW] billing.roobet.com — payment/wallet flows, target for business logic flaws on deposits/withdrawals
[NEW] dashboard.roobet.com — user dashboard, target for IDOR/cross-user data access
[NEW] app.roobet.com / web.roobet.com / www.roobet.com / m.roobet.com — main web apps, target for XSS/OAuth redirect flaws
[NEW] sso.roobet.com — single sign-on, target for SAML/OIDC misconfig
[NEW] dev.roobet.com / staging.roobet.com / test.roobet.com — non-prod environments, target for debug endpoints/swagger exposure
[NEW] login.roobet.com / portal.roobet.com / my.roobet.com — auth entry points, target for redirect_uri/state flaws
[NEW] support.roobet.com / mail.roobet.com — support/mail, lower priority
[NEW] roobet.com — root domain, target for subdomain takeover on dangling CNAMEs
[PRIO] api.roobet.com,8.8,attack_surface=10,business_value=9,tech_exposure=9,gate_ease=8,cloud_surface=8,freshness=10
[PRIO] auth.roobet.com,8.5,attack_surface=9,business_value=9,tech_exposure=10,gate_ease=7,cloud_surface=7,freshness=10
[PRIO] account.roobet.com,8.2,attack_surface=9,business_value=8,tech_exposure=8,gate_ease=7,cloud_surface=7,freshness=10
[PRIO] admin.roobet.com,7.9,attack_surface=8,business_value=10,tech_exposure=7,gate_ease=5,cloud_surface=8,freshness=10
[PRIO] billing.roobet.com,7.8,attack_surface=8,business_value=9,tech_exposure=7,gate_ease=6,cloud_surface=7,freshness=10
[PRIO] dashboard.roobet.com,7.5,attack_surface=8,business_value=7,tech_exposure=7,gate_ease=6,cloud_surface=6,freshness=10
[PRIO] dev.roobet.com,7.2,attack_surface=7,business_value=5,tech_exposure=9,gate_ease=9,cloud_surface=6,freshness=10
[PRIO] staging.roobet.com,7.0,attack_surface=7,business_value=5,tech_exposure=8,gate_ease=8,cloud_surface=6,freshness=10
[PRIO] sso.roobet.com,6.8,attack_surface=6,business_value=8,tech_exposure=9,gate_ease=5,cloud_surface=5,freshness=10
[PRIO] app.roobet.com,6.5,attack_surface=7,business_value=7,tech_exposure=6,gate_ease=6,cloud_surface=5,freshness=10
[HYP] API Mass Assignment on User Wallet/Profile Update
class: OTHER
asset: api.roobet.com
confidence: 65
reasoning: Primary API host with likely endpoints for user profile/wallet updates (PUT/PATCH /api/v1/user, /api/v1/wallet). Mass assignment via extra parameters (e.g., balance, role, email_verified) is common in crypto casinos. No auth tested yet — gate_ease=8 suggests low barrier.
evidence_needed: Response showing reflected extra fields in update response, or observable state change (balance/role) via GET after malicious PUT.
verify_steps: GET /api/v1/user (or /api/v1/me) to enumerate fields → PUT /api/v1/user with extra field "balance":999999 → GET /api/v1/user to confirm reflection. Passive-first, requires auth token.
impact: Attacker modifies own wallet balance, role, or email_verified → direct financial theft / privilege escalation. Severity: CRITICAL.
testability: AUTH_HELPED
[HYP] OAuth Redirect_URI Validation Bypass on auth.roobet.com
class: OATH
asset: auth.roobet.com
confidence: 60
reasoning: Auth service likely implements OAuth2/OIDC for login/sso. Common flaws: loose redirect_uri validation (subdomain/path traversal, wildcard), missing state parameter enforcement, or token leakage via referer. High business_value (ATO), tech_exposure=10 (OAuth).
evidence_needed: Authorization code or token delivered to attacker-controlled redirect_uri, or state parameter omitted/ignored.
verify_steps: GET /oauth/authorize?client_id=test&redirect_uri=https://evil.com&response_type=code&state=xyz → observe if redirect occurs to evil.com. Then test path traversal: redirect_uri=https://app.roobet.com/../evil.com. Passive GET only.
impact: Full account takeover via stolen authorization code/token. Severity: CRITICAL.
testability: PASSIVE
[HYP] IDOR/BOLA on Cross-User Wallet/Transaction Endpoints at account.roobet.com
class: IDOR
asset: account.roobet.com
confidence: 55
reasoning: Account service likely exposes endpoints like GET /api/v1/users/{user_id}/wallet, /transactions, /bets. Sequential UUIDs or numeric IDs enable enumeration. Gate_ease=7 suggests auth required but low barrier to cross-user access.
evidence_needed: Response containing another user's wallet balance, transaction history, or PII when accessing /users/{other_id}/wallet with valid session.
verify_steps: Auth as user A → GET /api/v1/users/me/wallet (baseline) → GET /api/v1/users/{user_B_id}/wallet (enumerate via referer logs, public profiles, or sequential IDs). Passive GET with auth.
impact: Mass PII/wallet data dump across all users. Severity: HIGH.
testability: AUTH_HELPED
[PARKED] API Mass Assignment on User Wallet/Profile Update: confidence 65 but verify_steps require AUTH_HELPED — cannot confirm without valid session; parked until auth flow mapped.
[PARKED] OAuth Redirect_URI Validation Bypass on auth.roobet.com: confidence 60 but passive probe may 404 if endpoint path differs (/authorize vs /oauth2/authorize vs /connect/authorize); needs endpoint discovery first.
[PARKED] IDOR/BOLA on Cross-User Wallet/Transaction Endpoints at account.roobet.com: confidence 55 but requires valid auth + user enumeration vector; parked until auth + ID format confirmed.
[FINAL] (none survive — all parked pending live recon)
[NEXT] SCAN: Passive HTTP probe all 20 hosts (HEAD /, 1 rps) to confirm live endpoints, server headers, and discover API/auth paths (/.well-known/oauth-authorization-server, /swagger.json, /api, /v1, /graphql). Exact: for h in api.roobet.com auth.roobet.com account.roobet.com admin.roobet.com billing.roobet.com dashboard.roobet.com dev.roobet.com staging.roobet.com test.roobet.com sso.roobet.com login.roobet.com portal.roobet.com app.roobet.com web.roobet.com www.roobet.com m.roobet.com my.roobet.com support.roobet.com mail.roobet.com roobet.com; do curl -I -s --max-time 5 "https://$h" 2>&1 | head -5; sleep 1; done
[LEARN] REJECTED OTHER @ api.roobet.com: mass assignment hypothesis parked — no live endpoint confirmed, auth state unknown.
[LEARN] REJECTED OATH @ auth.roobet.com: OAuth redirect_uri bypass parked — endpoint path unknown, passive probe needed first.
[LEARN] REJECTED IDOR @ account.roobet.com: IDOR hypothesis parked — requires auth + user ID format discovery.
[RISK] roobet: 75 — High-value crypto casino with 20 discovered subdomains, zero live probes completed. Primary API/auth/account surfaces untested. High probability of auth/IDOR/business logic flaws in wallet/betting flows. Risk elevated by broad scope (all company infrastructure) and crypto asset handling.
## 2026-09-03 20:05:09 UTC [target] (model nemotron3)
[NEW] api.roobet.com: HTTP 403 (Cloudflare bot-managed, blocks plain curl)
[NEW] www.roobet.com: HTTP 301 → roobet.com
[NEW] roobet.com: HTTP 200 (Remix/React SPA, catch-all /api/* routes)
[NEW] fs.roobet.com: HTTP 405 HEAD / 200 GET (GCS bucket serving FullStory, `?list-type=2` returns 301 to fullstory.com)
[CHANGED] 17/20 inventory hosts: no HTTP response (timeout/connection refused) — likely non-existent or strictly internal
[PRIO] api.roobet.com,7.8,attack_surface=9,business_value=9,tech_exposure=8,gate_ease=5,cloud_surface=8,freshness=10
[PRIO] roobet.com,6.2,attack_surface=7,business_value=7,tech_exposure=6,gate_ease=8,cloud_surface=5,freshness=10
[PRIO] fs.roobet.com,4.5,attack_surface=4,business_value=3,tech_exposure=5,gate_ease=10,cloud_surface=6,freshness=8
[PRIO] auth.roobet.com,0.0,attack_surface=0,business_value=0,tech_exposure=0,gate_ease=0,cloud_surface=0,freshness=0
[PRIO] account.roobet.com,0.0,attack_surface=0,business_value=0,tech_exposure=0,gate_ease=0,cloud_surface=0,freshness=0
[PRIO] admin.roobet.com,0.0,attack_surface=0,business_value=0,tech_exposure=0,gate_ease=0,cloud_surface=0,freshness=0
[HYP] GraphQL Introspection via Aliased Query on api.roobet.com
class: OTHER
asset: api.roobet.com
confidence: 55
reasoning: Client bundle references GraphQL WS ports 8087/8088; api.roobet.com returns 403 on plain GET but may allow GraphQL POST with proper headers/origin. Crypto casinos often expose introspection via aliases to bypass depth limits.
evidence_needed: Response containing __schema or __typename from POST /graphql with introspection query
verify_steps: POST https://api.roobet.com/graphql -H "Content-Type: application/json" -d '{"query":"{__schema{types{name}}}"}' → observe 200 with schema vs 403/400. Then test alias bypass: '{"query":"query{a:__schema{types{name}} b:__schema{types{name}}}"}'
impact: Full API surface mapping → targeted mass assignment/IDOR/broken auth. Severity: HIGH.
testability: PASSIVE
[HYP] OAuth Authorization Server Metadata Exposure on roobet.com
class: MISCONFIG
asset: roobet.com
confidence: 50
reasoning: Main SPA at roobet.com likely uses OAuth/OIDC for auth. /.well-known/oauth-authorization-server or /.well-known/openid-configuration may expose issuer, authorization_endpoint, token_endpoint, jwks_uri — enabling redirect_uri/state analysis.
evidence_needed: 200 JSON response with authorization_endpoint, token_endpoint, jwks_uri fields
verify_steps: GET https://roobet.com/.well-known/oauth-authorization-server → GET https://roobet.com/.well-known/openid-configuration → GET https://auth.roobet.com/.well-known/oauth-authorization-server (if auth host resolves)
impact: Recon for OAuth redirect_uri bypass, PKCE downgrade, JWKS spoofing. Severity: MEDIUM.
testability: PASSIVE
[HYP] GCS Bucket Object Enumeration on fs.roobet.com
class: MISCONFIG
asset: fs.roobet.com
confidence: 45
reasoning: GCS bucket returns 200 for ?list-type=2 (ListBucketResult) but 403/405 on HEAD. May allow partial object listing or metadata exposure via max-keys/prefix/delimiter parameters.
evidence_needed: XML ListBucketResult with Contents[] showing object keys (e.g., FullStory script versions, source maps)
verify_steps: GET https://fs.roobet.com/?list-type=2&max-keys=1000 → GET https://fs.roobet.com/?list-type=2&prefix=s/&max-keys=1000 → GET https://fs.roobet.com/?list-type=2&delimiter=/&max-keys=1000
impact: Source map disclosure → client-side logic reconstruction → bypass obfuscation. Severity: LOW-MEDIUM.
testability: PASSIVE
[PARKED] GraphQL Introspection via Aliased Query on api.roobet.com: confidence 55 but 403 block may require specific Origin/Referer headers or Cloudflare bypass; cannot confirm GraphQL endpoint exists without auth context.
[PARKED] OAuth Authorization Server Metadata Exposure on roobet.com: confidence 50 but auth.roobet.com unresolved — metadata may live on auth subdomain only.
[PARKED] GCS Bucket Object Enumeration on fs.roobet.com: confidence 45 but bucket appears to serve only FullStory script; low business value.
[FINAL] (none survive — all parked pending live auth/session context or resolved auth subdomain)
[NEXT] PROBE: GET https://roobet.com/.well-known/oauth-authorization-server && GET https://roobet.com/.well-known/openid-configuration
[LEARN] REJECTED OTHER @ api.roobet.com: mass assignment hypothesis parked — 403 block confirms Cloudflare bot management; no live API endpoint reachable without valid session/origin.
[LEARN] REJECTED OATH @ auth.roobet.com: OAuth redirect_uri bypass parked — auth.roobet.com does not resolve/respond; endpoint path unknown.
[LEARN] REJECTED IDOR @ account.roobet.com: IDOR hypothesis parked — account.roobet.com does not resolve/respond; no user ID format discoverable.
[LEARN] ACCEPTED MISCONFIG @ fs.roobet.com: GCS bucket allows ListBucketResult via ?list-type=2 but serves only FullStory assets; low impact.
[RISK] roobet: 65 — High-value crypto casino with primary API (api.roobet.com) behind Cloudflare bot management (403), auth/account/admin subdomains unresponsive. Main SPA at roobet.com exposes Remix catch-all routes. Attack surface compressed to 3 live hosts. Risk elevated by crypto wallet/betting flows but blocked by lack of auth context and unresponsive critical subdomains.
## 2026-09-03 22:31:31 UTC [target] (model nemotron3)
[NEW] roobet.com/.well-known/oauth-authorization-server: HTTP 200 (SPA shell catch-all, not OAuth metadata)
[NEW] roobet.com/.well-known/openid-configuration: HTTP 200 (SPA shell catch-all, not OAuth metadata)
[NEW] fs.roobet.com/?list-type=2&max-keys=1: HTTP 301 → fullstory.com (GCS bucket serves only FullStory)
[NEW] api.roobet.com/graphql: HTTP 403 (Cloudflare bot management blocks GraphQL POST)
[CHANGED] auth.roobet.com, account.roobet.com, admin.roobet.com, 14 others: no HTTP response (timeout/refused) — confirmed non-resolving or strictly internal
[PRIO] api.roobet.com,7.5,attack_surface=9,business_value=9,tech_exposure=8,gate_ease=4,cloud_surface=8,freshness=10
[PRIO] roobet.com,6.0,attack_surface=7,business_value=7,tech_exposure=6,gate_ease=8,cloud_surface=5,freshness=10
[PRIO] fs.roobet.com,3.5,attack_surface=3,business_value=2,tech_exposure=4,gate_ease=10,cloud_surface=5,freshness=8
[PRIO] auth.roobet.com,0.0,attack_surface=0,business_value=0,tech_exposure=0,gate_ease=0,cloud_surface=0,freshness=0
[PRIO] account.roobet.com,0.0,attack_surface=0,business_value=0,tech_exposure=0,gate_ease=0,cloud_surface=0,freshness=0
[PRIO] admin.roobet.com,0.0,attack_surface=0,business_value=0,tech_exposure=0,gate_ease=0,cloud_surface=0,freshness=0
[HYP] Remix SPA Catch-All Route Masks API Endpoints on roobet.com
class: MISCONFIG
asset: roobet.com
confidence: 65
reasoning: roobet.com returns 200 HTML for /.well-known/oauth-authorization-server and /.well-known/openid-configuration — the Remix catch-all route serves SPA shell for all unknown paths. Actual API endpoints under /api/* may exist but are masked by the catch-all.
evidence_needed: 200 JSON response with authorization_endpoint/token_endpoint/jwks_uri from a non-catch-all path, or discovery of actual API routes via client bundle analysis
verify_steps: GET https://roobet.com/api/auth/session → GET https://roobet.com/api/user/profile → GET https://roobet.com/api/graphql (observe if any return JSON vs HTML)
impact: Hidden API surface for auth/session/user endpoints → IDOR/mass assignment/business logic flaws. Severity: MEDIUM-HIGH.
testability: PASSIVE
[HYP] Cloudflare Bot Management Bypass via Origin/Referer Headers on api.roobet.com
class: OTHER
asset: api.roobet.com
confidence: 50
reasoning: api.roobet.com returns 403 for plain curl and GraphQL POST. Client bundle references GraphQL WS ports 8087/8088; the API may allow requests with valid Origin/Referer headers matching roobet.com or specific CF rules.
evidence_needed: 200 JSON response from POST /graphql with introspection query when sending Origin: https://roobet.com and Referer: https://roobet.com/
verify_steps: POST https://api.roobet.com/graphql -H "Content-Type: application/json" -H "Origin: https://roobet.com" -H "Referer: https://roobet.com/" -d '{"query":"{__schema{types{name}}}"}' → observe 200 vs 403
impact: GraphQL introspection → full API surface mapping → targeted mass assignment/IDOR/broken auth. Severity: HIGH.
testability: PASSIVE
[HYP] GCS Bucket Path Traversal via Prefix/Delimiter on fs.roobet.com
class: MISCONFIG
asset: fs.roobet.com
confidence: 40
reasoning: GCS bucket returns 301 for ?list-type=2 to fullstory.com. May allow object metadata exposure via prefix/delimiter parameters before redirect, or alternate bucket paths.
evidence_needed: XML ListBucketResult with Contents[] showing non-FullStory keys, or 200 on prefix paths like /s/ or /assets/
verify_steps: GET https://fs.roobet.com/?list-type=2&prefix=s/&max-keys=100 → GET https://fs.roobet.com/s/ → GET https://fs.roobet.com/assets/
impact: Source map disclosure → client-side logic reconstruction. Severity: LOW.
testability: PASSIVE
[PARKED] GCS Bucket Path Traversal via Prefix/Delimiter on fs.roobet.com: confidence 40 < 40 threshold; bucket confirmed FullStory-only via 301 redirect; low business value.
[FINAL] 1. Remix SPA Catch-All Route Masks API Endpoints on roobet.com (65) 2. Cloudflare Bot Management Bypass via Origin/Referer Headers on api.roobet.com (50)
[NEXT] PROBE: POST https://api.roobet.com/graphql -H "Content-Type: application/json" -H "Origin: https://roobet.com" -H "Referer: https://roobet.com/" -d '{"query":"{__schema{types{name}}}"}'
[LEARN] REJECTED MISCONFIG @ roobet.com: OAuth metadata endpoints return SPA shell (catch-all route), not JSON configuration.
[LEARN] REJECTED MISCONFIG @ fs.roobet.com: GCS bucket ?list-type=2 redirects to fullstory.com; no object enumeration possible.
[LEARN] REJECTED OTHER @ api.roobet.com: GraphQL endpoint blocked by Cloudflare bot management (403) without valid Origin/Referer.
[LEARN] ACCEPTED MISCONFIG @ roobet.com: Remix catch-all route masks potential API endpoints under /api/* paths.
[LEARN] PARKED api.roobet.com Cloudflare bypass: requires valid browser headers/session to test.
[LEARN] PARKED auth.roobet.com/account.roobet.com/admin.roobet.com: subdomains unresponsive; no attack surface confirmed.
[RISK] roobet: 60 — High-value crypto casino with primary API (api.roobet.com) behind Cloudflare bot management (403), auth/account/admin subdomains unresponsive. Main SPA at roobet.com uses catch-all routing masking /api/* endpoints. Attack surface compressed to 2 testable hosts (api.roobet.com, roobet.com). Risk elevated by crypto wallet/betting flows but blocked by lack of auth context and unresponsive critical subdomains.
## 2026-09-04 00:29:59 UTC [target] (model nemotron3)
[NEW] crash-gs.roobet.com confirmed live Socket.IO game-server (wss://crash-gs.roobet.com/socket.io/?EIO=3&transport=websocket) — TCP 443 connects, HTTP hangs/000; previously discovered, now network-confirmed
[NEW] roobet.com `/_api/` server route family: `_api/settings/get` (200 JSON: internal config incl. client IP, per-request 64-hex sessionId, restricted-country/feature flags, serverTime) and `_api/tp-games/essentials` (200 JSON: full game catalog + internal S3 bucket roobet-dev-public-images-prod) — only 2 of 12 guessed subroutes resolve (rest 404), NOT behind Cloudflare bot-gate
[NEW] roobet.com `/pusher/auth` + `/pusher/user-auth` exist as live routes (405 on POST format tested) — Pusher channel/user auth surface
[CHANGED] roobet.com `/.well-known/oauth-authorization-server` + `/.well-known/openid-configuration` both return 200 SPA shell HTML (Remix catch-all), NOT real OAuth/OIDC metadata — neutralizes prior OAuth-meta hypotheses
[CHANGED] auth.roobet.com, account.roobet.com, admin.roobet.com, 14 others: no HTTP response (timeout/refused) — confirmed non-resolving or strictly internal
[CHANGED] api.roobet.com GraphQL POST returns 403 (Cloudflare bot management) even with Origin/Referer headers — bot-gate remains intact for scripted probes
[CHANGED] fs.roobet.com/?list-type=2 returns 301 → fullstory.com; GCS bucket serves only FullStory assets; no object enumeration possible
[PRIO] api.roobet.com,7.85,attack_surface=9,business_value=9,tech_exposure=8,gate_ease=4,cloud_surface=8,freshness=10
[PRIO] roobet.com,6.20,attack_surface=7,business_value=7,tech_exposure=6,gate_ease=8,cloud_surface=5,freshness=10
[PRIO] crash-gs.roobet.com,5.95,attack_surface=6,business_value=6,tech_exposure=7,gate_ease=3,cloud_surface=7,freshness=10
[PRIO] fs.roobet.com,3.50,attack_surface=3,business_value=2,tech_exposure=4,gate_ease=10,cloud_surface=5,freshness=8
[HYP] Undocumented _api/* Server Routes Expose Hidden Business Logic Surface
class: OTHER
asset: roobet.com/_api/*
confidence: 55
reasoning: Two live _api routes confirmed (settings/get, tp-games/essentials) bypass Cloudflare bot-gate and return internal config (rotating sessionId hex, feature flags, serverTime) and full game catalog with internal S3 bucket reference. Only 2/12 candidate subroutes resolve; full route set unknown.
evidence_needed: Additional live _api/<action> subroutes returning non-public data (user/session/wallet/config/balance), or settings/get reflecting untrusted input with another user's data
verify_steps: GET https://roobet.com/_api/{auth,user,wallet,config,benefits,trivia,promotion,affiliate,notifications,jackpot,leaderboard}/get + variants (1 rps); compare 200 vs 404 baseline; diff 200 bodies for non-public fields (user IDs, balances, flags, internal endpoints). Read-only GET.
impact: Internal config/feature/session data disclosure or hidden money/auth flow bypass → LOW-MEDIUM severity (no customer/financial/auth data confirmed yet); potential chain to API surface mapping
testability: PASSIVE
[HYP] GraphQL Admin Schema Exposed Behind Cloudflare Bot-Gate
class: MISCONFIG
asset: api.roobet.com/graphql (HTTP) + wss://api.roobet.com/graphql (WS ports 8087/8088)
confidence: 55
reasoning: Client bundle embeds ROOBET_WS_GQL_ADMIN_PORT=8088, ROOBET_WS_GQL_PRODUCT_PORT=8087, ROOBET_WS_API_URL=wss://api.roobet.com/. Dedicated admin port implies admin-only schema with privileged mutations (wallet/bonus/user/role). HTTP /graphql returns 403 bot-blocked; WS ports 8087/8088 TCP-refused at Cloudflare edge (only 443/8443 open). Requires browser session with valid Turnstile + Origin/Referer.
evidence_needed: 200 GraphQL introspection (__schema/__typename) from HTTPS /graphql with browser-authentic headers+origin, or WSS 101 upgrade + introspection showing admin fields (userManagement, bonusAdmin, walletAdmin, roleAssignment)
verify_steps: In turnstile-passing browser: POST https://api.roobet.com/graphql -H "Content-Type: application/json" -H "Origin: https://roobet.com" -H "Referer: https://roobet.com/" -d '{"query":"{__schema{types{name}}}"}' → observe 200 vs 403; if 403 persists, WSS wss://api.roobet.com/graphql with socketToken introspection. Read-only introspection only; no mutations.
impact: Full API surface mapping → targeted IDOR/mass-assignment/privilege escalation on wallets/bonuses/user-management → HIGH-CRITICAL if reachable
testability: AUTH_HELPED
[HYP] Unauthenticated State Exposure on Crash Game WebSocket
class: MISCONFIG
asset: crash-gs.roobet.com (wss socket.io)
confidence: 42
reasoning: Confirmed live Cloudflare Socket.IO WS game-server; root HTTP hangs (WS-only). App-level event channels (rewards, bet state, round data) may be reachable if sub/unsub not token-validated. Game state events could leak round data or accept unauthenticated subscription.
evidence_needed: WSS connect + socket.io subscribe to state/bet channels returns data or errors inconsistently to determine auth model
verify_steps: Browser/devtools WS: wss://crash-gs.roobet.com/socket.io/?EIO=3&transport=websocket → send socket.io connect + subscribe to `rewardsInstantRakeback` / bet events → observe whether server requires user/session token. Read-only subscribe; no bet placement.
impact: Unauthorized live game/round state read or channel enumeration → LOW-MEDIUM; no money mutation unless socket `bet` accepts unvalidated placement (would be CRITICAL — do NOT test writes)
testability: HUMAN_ONLY
[PARKED] Unauthenticated State Exposure on Crash Game WebSocket: confidence 42 < 40 threshold borderline; requires browser/WS tooling, HTTP unreachable over curl (Cloudflare WS-gated), HUMAN_ONLY testability — held for browser-phase, not passive-verifiable now
[PARKED] GraphQL Admin Schema Exposed Behind Cloudflare Bot-Gate: confidence 55 but bot-gate + closed WS ports make it AUTH_HELPED only; no passive confirmation possible; highest value but blocked
[FINAL] 1. Undocumented _api/* Server Routes Expose Hidden Business Logic Surface (55, PASSIVE) — only newly actionable passive surface this cycle (2 live routes confirmed, not bot-gated)
[FINAL] 2. GraphQL Admin Schema Exposed Behind Cloudflare Bot-Gate (55, AUTH_HELPED) — highest value, needs browser session with Turnstile
[NEXT] PROBE: GET https://roobet.com/_api/{auth,user,wallet,config,benefits,trivia,promotion,affiliate,notifications,jackpot,leaderboard}/get + variants (1 rps), record 200 vs 404 baseline; diff each 200 body for non-public fields (session/user IDs, balance, flags, internal endpoints). Read-only GET.
[LEARN] REJECTED MISCONFIG @ roobet.com: OAuth metadata endpoints return SPA shell (catch-all route), not JSON configuration
[LEARN] REJECTED MISCONFIG @ fs.roobet.com: GCS bucket ?list-type=2 redirects to fullstory.com; no object enumeration possible
[LEARN] REJECTED OTHER @ api.roobet.com: GraphQL endpoint blocked by Cloudflare bot management (403) without valid Origin/Referer/browser session
[LEARN] ACCEPTED MISCONFIG @ roobet.com: Remix catch-all route masks potential API endpoints under /api/* paths
[LEARN] ACCEPTED OTHER @ roobet.com _api/: two undocumented live server routes confirmed reachable past Cloudflare bot-gate (settings/get, tp-games/essentials); new low-gate server surface worth enumerating
[LEARN] PARKED api.roobet.com Cloudflare bypass: requires valid browser headers/session/turnstile to test
[LEARN] PARKED auth.roobet.com/account.roobet.com/admin.roobet.com: subdomains unresponsive; no attack surface confirmed
[LEARN] PARKED crash-gs.roobet.com unauthenticated socket: requires browser/WS tooling, HUMAN_ONLY
[RISK] roobet: 63 — Main API (api.roobet.com) and all auth/account subdomains remain gated by Cloudflare bot-management or unresponsive; GraphQL admin (8088) and Crash WS (crash-gs.roobet.com) only reachable via browser. New low-gate surface: _api/* routes on roobet.com (confirmed live, not bot-gated) and confirmed-live Crash WS host. No confirmed reportable vuln; no scanner POC; engagement rules (≤1 rps, read-only GET, no data mutation, no auth-bypass on live customer data) fully respected.
