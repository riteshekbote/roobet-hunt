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
