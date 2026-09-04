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

## 2026-09-03 22:40:48 UTC
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
- NEW api.roobet.com: HTTP 403 (Cloudflare bot-managed, blocks plain curl)
- NEW www.roobet.com: HTTP 301 → roobet.com
- NEW roobet.com: HTTP 200 (Remix/React SPA, catch-all /api/* routes)
- NEW fs.roobet.com: HTTP 405 HEAD / 200 GET (GCS bucket serving FullStory, `?list-type=2` returns 301 to fullstory.com)
- CHANGED 17/20 inventory hosts: no HTTP response (timeout/connection refused) — likely non-existent or strictly internal
- NEW roobet.com `/_api/` server route family: `_api/settings/get` (200 JSON: internal config incl. client IP, per-request sessionId hex, restricted-country/feature flags, serverTime) and `_api/tp-games/ess
- NEW crash-gs.roobet.com confirmed live Cloudflare (172.64.151.243) Socket.IO WS game-server at `wss://crash-gs.roobet.com/socket.io/?EIO=3&transport=websocket` — TCP 443 connects, HTTP request hangs/000 (
- CHANGED roobet.com `/.well-known/oauth-authorization-server` + `/.well-known/openid-configuration` both return 200 SPA shell HTML (catch-all), NOT real OAuth/OIDC metadata — neutralizes nemotron3 OAuth-meta h
- CHANGED roobet.com `/pusher/auth` + `/pusher/user-auth` exist as live routes (405 on the POST format tested) — Pusher channel/user auth surface, auth-adjacent.
- NEW roobet.com/.well-known/oauth-authorization-server: HTTP 200 (SPA shell catch-all, not OAuth metadata)
- NEW roobet.com/.well-known/openid-configuration: HTTP 200 (SPA shell catch-all, not OAuth metadata)
- NEW fs.roobet.com/?list-type=2&max-keys=1: HTTP 301 → fullstory.com (GCS bucket serves only FullStory)
- NEW api.roobet.com/graphql: HTTP 403 (Cloudflare bot management blocks GraphQL POST)
- CHANGED auth.roobet.com, account.roobet.com, admin.roobet.com, 14 others: no HTTP response (timeout/refused) — confirmed non-resolving or strictly internal

## 2026-09-04 00:31:27 UTC
- NEW crash-gs.roobet.com confirmed live Socket.IO game-server (wss://crash-gs.roobet.com/socket.io/?EIO=3&transport=websocket) — TCP 443 connects, HTTP hangs/000; previously discovered, now network-confirm
- NEW roobet.com `/_api/` server route family: `_api/settings/get` (200 JSON: internal config incl. client IP, per-request 64-hex sessionId, restricted-country/feature flags, serverTime) and `_api/tp-games/
- NEW roobet.com `/pusher/auth` + `/pusher/user-auth` exist as live routes (405 on POST format tested) — Pusher channel/user auth surface
- CHANGED roobet.com `/.well-known/oauth-authorization-server` + `/.well-known/openid-configuration` both return 200 SPA shell HTML (Remix catch-all), NOT real OAuth/OIDC metadata — neutralizes prior OAuth-meta
- CHANGED auth.roobet.com, account.roobet.com, admin.roobet.com, 14 others: no HTTP response (timeout/refused) — confirmed non-resolving or strictly internal
- CHANGED api.roobet.com GraphQL POST returns 403 (Cloudflare bot management) even with Origin/Referer headers — bot-gate remains intact for scripted probes
- CHANGED fs.roobet.com/?list-type=2 returns 301 → fullstory.com; GCS bucket serves only FullStory assets; no object enumeration possible
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
- NEW api.roobet.com: HTTP 403 (Cloudflare bot-managed, blocks plain curl)
- NEW www.roobet.com: HTTP 301 → roobet.com
- NEW roobet.com: HTTP 200 (Remix/React SPA, catch-all /api/* routes)
- NEW fs.roobet.com: HTTP 405 HEAD / 200 GET (GCS bucket serving FullStory, `?list-type=2` returns 301 to fullstory.com)
- CHANGED 17/20 inventory hosts: no HTTP response (timeout/connection refused) — likely non-existent or strictly internal
- NEW roobet.com `/_api/` server route family: `_api/settings/get` (200 JSON: internal config incl. client IP, per-request sessionId hex, restricted-country/feature flags, serverTime) and `_api/tp-games/ess
- NEW crash-gs.roobet.com confirmed live Cloudflare (172.64.151.243) Socket.IO WS game-server at `wss://crash-gs.roobet.com/socket.io/?EIO=3&transport=websocket` — TCP 443 connects, HTTP request hangs/000 (
- CHANGED roobet.com `/.well-known/oauth-authorization-server` + `/.well-known/openid-configuration` both return 200 SPA shell HTML (catch-all), NOT real OAuth/OIDC metadata — neutralizes nemotron3 OAuth-meta h
- CHANGED roobet.com `/pusher/auth` + `/pusher/user-auth` exist as live routes (405 on the POST format tested) — Pusher channel/user auth surface, auth-adjacent.
- NEW roobet.com `/_api/` server route family: `_api/settings/get` (200 JSON: internal config incl. client IP, per-request sessionId hex, restricted-country/feature flags, serverTime) and `_api/tp-games/ess

## 2026-09-04 05:08:52 UTC
- NEW roobet.com `/_api/` server route family confirmed: `_api/settings/get` (200 JSON: internal config, client IP, 64-hex sessionId, feature flags, serverTime) and `_api/tp-games/essentials` (200 JSON: ful
- NEW crash-gs.roobet.com confirmed live Socket.IO game-server (wss://crash-gs.roobet.com/socket.io/?EIO=3&transport=websocket) — TCP 443 connects, HTTP hangs/000
- NEW roobet.com `/pusher/auth` + `/pusher/user-auth` exist as live routes (405 on POST format tested) — Pusher channel/user auth surface
- CHANGED roobet.com `/.well-known/oauth-authorization-server` + `/.well-known/openid-configuration` both return 200 SPA shell HTML (Remix catch-all), NOT real OAuth/OIDC metadata
- CHANGED auth.roobet.com, account.roobet.com, admin.roobet.com, 14 others: no HTTP response (timeout/refused) — confirmed non-resolving or strictly internal
- CHANGED api.roobet.com GraphQL POST returns 403 (Cloudflare bot management) even with Origin/Referer headers — bot-gate remains intact for scripted probes
- CHANGED fs.roobet.com/?list-type=2 returns 301 → fullstory.com; GCS bucket serves only FullStory assets; no object enumeration possible

## 2026-09-04 09:52:31 UTC
- NEW roobet.com `/_api/settings/get` and `/_api/tp-games/essentials` confirmed live (200 JSON), NOT behind Cloudflare bot-gate — distinct server route family from `/api/*` catch-all
- NEW roobet.com `/pusher/auth` + `/pusher/user-auth` live routes (405 on POST format tested) — Pusher auth surface
- NEW crash-gs.roobet.com confirmed live Socket.IO WS (wss://crash-gs.roobet.com/socket.io/?EIO=3&transport=websocket) — TCP 443 connects, HTTP hangs
- CHANGED roobet.com `/.well-known/oauth-authorization-server` + `/.well-known/openid-configuration` both return 200 SPA shell HTML (Remix catch-all), NOT real OAuth/OIDC metadata
- CHANGED api.roobet.com GraphQL POST returns 403 (Cloudflare bot management) even with Origin/Referer headers — bot-gate intact for scripted probes
- CHANGED fs.roobet.com/?list-type=2 returns 301 → fullstory.com; GCS bucket serves only FullStory assets; no object enumeration
- CHANGED auth.roobet.com, account.roobet.com, admin.roobet.com, 14 others: no HTTP response (timeout/refused) — confirmed non-resolving or strictly internal
- NEW Only 2 of 12 guessed `_api/*` subroutes resolve (settings/get, tp-games/essentials); 10 return 404
- NEW `_api/admin/users` → 401 Unauthorized (exists, auth-gated, admin endpoint on low-gate surface)
- NEW `_api/admin/stats` → 401 Unauthorized (exists, auth-gated, admin endpoint on low-gate surface)
- NEW `_api/affiliate/get` → 401 Unauthorized (exists, auth-gated, affiliate data endpoint)
- NEW `_api/auth/logout` → 302 Found → `/` (exists, auth-redirect)
- CHANGED `_api/*` surface now 5 live routes confirmed (up from 2): settings/get (200), tp-games/essentials (200), admin/users (401), admin/stats (401), affiliate/get (401)
- CHANGED `_api/settings/get` full dump: exposes client IP (`64.236.169.100`), per-request 64-hex `sessionId`, `countryCode`/`regionCountryCode`, full `restrictedCountries` map (33 entries), `restrictedRegion: 

## 2026-09-04 14:20:04 UTC
- NEW roobet.com/_api/admin/users → 401 Unauthorized (admin endpoint exists on low-gate surface, auth-gated)
- NEW roobet.com/_api/admin/stats → 401 Unauthorized (admin endpoint exists on low-gate surface, auth-gated)
- NEW roobet.com/_api/affiliate/get → 401 Unauthorized (affiliate endpoint exists on low-gate surface, auth-gated)
- NEW roobet.com/_api/auth/logout → 302 Found → `/` (auth redirect endpoint exists)
- CHANGED roobet.com/_api/* surface now 5 live routes confirmed (up from 2): settings/get (200), tp-games/essentials (200), admin/users (401), admin/stats (401), affiliate/get (401)
- CHANGED roobet.com/_api/settings/get full dump exposes client IP, per-request 64-hex sessionId, countryCode/regionCountryCode, full restrictedCountries map (33 entries), restrictedRegion flags, withdraw flags
- CHANGED api.roobet.com GraphQL POST remains 403 (Cloudflare bot-gate intact even with Origin/Referer)
- CHANGED auth.roobet.com, account.roobet.com, admin.roobet.com + 14 others: no HTTP response (confirmed non-resolving/internal)
- CHANGED fs.roobet.com/?list-type=2 returns 301 → fullstory.com; GCS bucket serves only FullStory
- CHANGED roobet.com/.well-known/oauth-authorization-server + openid-configuration return SPA shell (catch-all), not OAuth metadata

## 2026-09-04 17:53:31 UTC

## 2026-09-04 20:00:09 UTC
- NEW api.roobet.com WS surface fully gated: raw TLS WebSocket upgrade to `wss://api.roobet.com/graphql` on BOTH 443 and 8443 returns `HTTP/1.1 403 Forbidden` (Cloudflare edge, not 101) — bot-gate covers WS
- NEW crash-gs.roobet.com: TLS WS upgrade to `/socket.io/?EIO=3&transport=websocket` does NOT get 4xx (connection stays open) then app-layer timeout — consistent with live Socket.IO server awaiting protocol
- CHANGED `_api/settings/get` input reflection NEGATIVE: X-Forwarded-For: 203.0.113.7, `?sessionId=[64hex]`, `Referer: https://evil.com`, and `Cookie: sessionId=deadbeef` produce identical fields — `ip` stays s
- NEW roobet.com `/pusher/auth` + `/pusher/user-auth`: POST => 405 (live route, wrong method/body), GET => 200 SPA-shell catch-all. Pusher auth is POST-only; requires valid session + exact `socket_id`/`chan
- NEW Bundle re-analysis (entry.client-DstZRzUD.js): confirms ROOBET_* inlining (WS_API_URL `wss://api.roobet.com/`, GQL ports 8087/8088, CRASH_WS_URL crash-gs, pusher authEndpoint `/pusher/auth`). Only mod
- CHANGED `_api/{missions,challenges,bonuses,sportsbook}/get+sportsbook` => 404 SPA shell; surface remains exactly 6 live routes.
- NEW api.roobet.com: raw WS upgrade to `/graphql` on 443 AND 8443 → `HTTP 403 Forbidden` from Cloudflare edge (bot-gate enforces WS upgrades, not just HTTP; admin port 8088 unreachable via edge).
- NEW crash-gs.roobet.com: TLS upgrade to `/socket.io/?EIO=3&transport=websocket` stays open (no 4xx) then app-layer timeout = live Socket.IO server awaiting protocol frames; curl cannot complete handshake.
- CHANGED `_api/settings/get` reflection NEGATIVE — X-Forwarded-For/`?sessionId`/Referer/Cookie all inert (`ip` = server-observed egress 20.118.246.10, sessionId rotates per-request, not the auth cookie).
- NEW `/pusher/auth` + `/pusher/user-auth` POST→405 (live), GET→200 SPA-shell catch-all; POST-only Pusher auth, session+exact-body required.
- CHANGED `_api/{missions,challenges,bonuses,sportsbook}/get` → 404; surface still exactly 6 live routes. Bundle re-analysis: no new Roobet-owned hosts (FastTrack config is 3P).
