# Roobet inventory (discovery seed 2026-09-02)
# NOTE: hosts below are discovery candidates from passive DNS/CT; confirm in-scope vs program scope before active testing.
account.roobet.com
admin.roobet.com
api.roobet.com
app.roobet.com
auth.roobet.com
billing.roobet.com
dashboard.roobet.com
dev.roobet.com
login.roobet.com
m.roobet.com
mail.roobet.com
my.roobet.com
portal.roobet.com
roobet.com
sso.roobet.com
staging.roobet.com
support.roobet.com
test.roobet.com
web.roobet.com
www.roobet.com

## PASSIVE RECON 2026-09-02 (read-only, non-intrusive)

> Recon observations only. These are NOT confirmed vulnerabilities; ownership/in-scope of each host must be confirmed against the program scope before any active testing. Hosts resolve + serve HTTP — investigation requires scoped authorization.

**Probed:** 20 hosts | **Live HTTP:** 0

| Host | Status | Server/Tech |
|---|---|---|

## 2026-09-02 21:54:54 UTC

## 2026-09-02 23:55:46 UTC

## 2026-09-03 03:47:00 UTC

## 2026-09-03 08:51:33 UTC

## 2026-09-03 13:28:47 UTC

## 2026-09-03 17:18:26 UTC
- NEW `fs.roobet.com` (34.8.116.253, non-Cloudflare GCP/GCS host, 200, serves FullStory `/s/fs.js`) — absent from inventory.
- NEW `crash-gs.roobet.com` (Cloudflare, Crash game-server, wss/socket.io) — absent from inventory.
- CHANGED `api.roobet.com` confirmed Cloudflare bot-managed: plain curl => 403 block; GraphQL WS ports 8087(product)/8088(admin) embedded in client bundle but NOT externally reachable (Cloudflare exposes only 4
- CHANGED `roobet.com` is Remix/React SPA; all `/api/*` server-differentiables absent (200 SPA shell catch-all).
- NEW api.roobet.com — primary API surface, high-value target for auth/IDOR/SSRF/mass-assignment
- NEW auth.roobet.com — authentication/authorization service, target for OAuth/JWT/session flaws
- NEW account.roobet.com — user account management, target for IDOR/BOLA on wallet/profile endpoints
- NEW admin.roobet.com — admin panel candidate, target for auth bypass/privilege escalation
- NEW billing.roobet.com — payment/wallet flows, target for business logic flaws on deposits/withdrawals
- NEW dashboard.roobet.com — user dashboard, target for IDOR/cross-user data access
- NEW app.roobet.com / web.roobet.com / www.roobet.com / m.roobet.com — main web apps, target for XSS/OAuth redirect flaws
- NEW sso.roobet.com — single sign-on, target for SAML/OIDC misconfig
- NEW dev.roobet.com / staging.roobet.com / test.roobet.com — non-prod environments, target for debug endpoints/swagger exposure
- NEW login.roobet.com / portal.roobet.com / my.roobet.com — auth entry points, target for redirect_uri/state flaws
- NEW support.roobet.com / mail.roobet.com — support/mail, lower priority
- NEW roobet.com — root domain, target for subdomain takeover on dangling CNAMEs

## 2026-09-03 20:05:21 UTC
- NEW api.roobet.com: HTTP 403 (Cloudflare bot-managed, blocks plain curl)
- NEW www.roobet.com: HTTP 301 → roobet.com
- NEW roobet.com: HTTP 200 (Remix/React SPA, catch-all /api/* routes)
- NEW fs.roobet.com: HTTP 405 HEAD / 200 GET (GCS bucket serving FullStory, `?list-type=2` returns 301 to fullstory.com)
- CHANGED 17/20 inventory hosts: no HTTP response (timeout/connection refused) — likely non-existent or strictly internal
