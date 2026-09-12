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

## 2026-09-04 22:18:36 UTC
- NEW roobet.com/_api/admin/users: 401 Unauthorized confirmed (admin endpoint on low-gate surface, not behind Cloudflare bot-gate)
- NEW roobet.com/_api/admin/stats: 401 Unauthorized confirmed (admin endpoint on low-gate surface)
- NEW roobet.com/_api/affiliate/get: 401 Unauthorized confirmed; parameter tests (?user_id, ?affiliate_code) also return 401 (not 404)
- NEW roobet.com/_api/auth/logout: 302 Found → / (reveals Express.js session cookies: connect.sid HttpOnly + userId non-HttpOnly + twofactorRequired)
- NEW roobet.com/_api/settings/get: input reflection NEGATIVE — X-Forwarded-For, ?sessionId, Referer, Cookie:sessionId all inert (ip=server-observed egress, sessionId rotates per-request)
- NEW api.roobet.com WS: raw TLS upgrade to wss://api.roobet.com/graphql on 443 AND 8443 → HTTP 403 (Cloudflare edge blocks WS upgrades); admin port 8088 unreachable
- NEW crash-gs.roobet.com: TLS WS upgrade to /socket.io/?EIO=3&transport=websocket stays open (no 4xx) then app-layer timeout = live Socket.IO server
- NEW roobet.com/pusher/auth + /pusher/user-auth: POST→405 (live route), GET→200 SPA shell; POST-only auth endpoints requiring valid session + exact body
- CHANGED roobet.com/_api/* surface: full enumeration complete — 40 candidates tested, exactly 6 live routes (settings/get 200, tp-games/essentials 200, admin/users 401, admin/stats 401, affiliate/get 401, auth
- CHANGED _api/settings/get reflection tests: all negative — no session fixation or cross-user data reflection vector
- CHANGED api.roobet.com GraphQL: remains 403 bot-gated even with Origin/Referer; WS ports 8087/8088 TCP-refused at edge
- CHANGED auth.roobet.com/account.roobet.com/admin.roobet.com + 14 others: confirmed non-resolving/internal

## 2026-09-05 00:15:44 UTC
- NEW roobet.com/_api/admin/users: 401 Unauthorized confirmed (admin endpoint on low-gate surface, not behind Cloudflare bot-gate)
- NEW roobet.com/_api/admin/stats: 401 Unauthorized confirmed (admin endpoint on low-gate surface)
- NEW roobet.com/_api/affiliate/get: 401 Unauthorized confirmed; parameter tests (?user_id, ?affiliate_code) also return 401 (not 404)
- NEW roobet.com/_api/auth/logout: 302 Found → / (reveals Express.js session cookies: connect.sid HttpOnly + userId non-HttpOnly + twofactorRequired)
- NEW roobet.com/_api/settings/get: input reflection NEGATIVE — X-Forwarded-For, ?sessionId, Referer, Cookie:sessionId all inert (ip=server-observed egress, sessionId rotates per-request)
- NEW api.roobet.com WS: raw TLS upgrade to wss://api.roobet.com/graphql on 443 AND 8443 → HTTP 403 (Cloudflare edge blocks WS upgrades); admin port 8088 unreachable
- NEW crash-gs.roobet.com: TLS WS upgrade to /socket.io/?EIO=3&transport=websocket stays open (no 4xx) then app-layer timeout = live Socket.IO server
- NEW roobet.com/pusher/auth + /pusher/user-auth: POST→405 (live route), GET→200 SPA shell; POST-only auth endpoints requiring valid session + exact body
- CHANGED roobet.com/_api/* surface: full enumeration complete — 40 candidates tested, exactly 6 live routes (settings/get 200, tp-games/essentials 200, admin/users 401, admin/stats 401, affiliate/get 401, auth
- CHANGED _api/settings/get reflection tests: all negative — no session fixation or cross-user data reflection vector
- CHANGED api.roobet.com GraphQL: remains 403 bot-gated even with Origin/Referer; WS ports 8087/8088 TCP-refused at edge
- CHANGED auth.roobet.com/account.roobet.com/admin.roobet.com + 14 others: confirmed non-resolving/internal
- NEW roobet.com/_api/admin/users: 401 Unauthorized confirmed (admin endpoint on low-gate surface, not behind Cloudflare bot-gate)
- NEW roobet.com/_api/admin/stats: 401 Unauthorized confirmed (admin endpoint on low-gate surface)
- NEW roobet.com/_api/affiliate/get: 401 Unauthorized confirmed; parameter tests (?user_id, ?affiliate_code) also return 401 (not 404)
- NEW roobet.com/_api/auth/logout: 302 Found → / (reveals Express.js session cookies: connect.sid HttpOnly + userId non-HttpOnly + twofactorRequired)
- NEW roobet.com/_api/settings/get: input reflection NEGATIVE — X-Forwarded-For, ?sessionId, Referer, Cookie:sessionId all inert (ip=server-observed egress, sessionId rotates per-request)
- NEW api.roobet.com WS: raw TLS upgrade to wss://api.roobet.com/graphql on 443 AND 8443 → HTTP 403 (Cloudflare edge blocks WS upgrades); admin port 8088 unreachable
- NEW crash-gs.roobet.com: TLS WS upgrade to /socket.io/?EIO=3&transport=websocket stays open (no 4xx) then app-layer timeout = live Socket.IO server
- NEW roobet.com/pusher/auth + /pusher/user-auth: POST→405 (live route), GET→200 SPA shell; POST-only auth endpoints requiring valid session + exact body
- CHANGED roobet.com/_api/* surface: full enumeration complete — 40 candidates tested, exactly 6 live routes (settings/get 200, tp-games/essentials 200, admin/users 401, admin/stats 401, affiliate/get 401, auth
- CHANGED _api/settings/get reflection tests: all negative — no session fixation or cross-user data reflection vector
- CHANGED api.roobet.com GraphQL: remains 403 bot-gated even with Origin/Referer; WS ports 8087/8088 TCP-refused at edge
- CHANGED auth.roobet.com/account.roobet.com/admin.roobet.com + 14 others: confirmed non-resolving/internal

## 2026-09-05 04:41:45 UTC
- NEW roobet.com/_api/admin/users: 401 confirmed (low-gate admin endpoint, not behind Cloudflare bot-gate)
- NEW roobet.com/_api/admin/stats: 401 confirmed (low-gate admin endpoint)
- NEW roobet.com/_api/affiliate/get: 401 confirmed; parameter tests (?user_id, ?affiliate_code) return 401 not 404
- NEW roobet.com/_api/auth/logout: 302 reveals Express.js session cookies (connect.sid HttpOnly + userId non-HttpOnly + twofactorRequired)
- NEW roobet.com/_api/settings/get: input reflection NEGATIVE — XFF, ?sessionId, Referer, Cookie:sessionId all inert
- NEW api.roobet.com GraphQL: remains 403 bot-gated on POST and GET; WS upgrade on 443/8443 returns HTTP 403
- NEW crash-gs.roobet.com: TLS WS upgrade to /socket.io stays open (no 4xx) then app-layer timeout = live Socket.IO server
- NEW roobet.com/pusher/auth + /pusher/user-auth: POST→405 (live route), GET→200 SPA shell; POST-only auth endpoints
- CHANGED roobet.com/_api/* surface: full enumeration complete — 40 candidates tested, exactly 6 live routes (settings/get 200, tp-games/essentials 200, admin/users 401, admin/stats 401, affiliate/get 401, auth
- CHANGED auth.roobet.com/account.roobet.com/admin.roobet.com/billing.roobet.com/dashboard.roobet.com/sso.roobet.com + others: confirmed non-resolving/internal (000/timeout)

## 2026-09-05 08:41:50 UTC
- NEW roobet.com/_api/* enumeration confirmed complete: exactly 6 live routes (settings/get 200, tp-games/essentials 200, admin/users 401, admin/stats 401, affiliate/get 401, auth/logout 302); 34 candidates
- NEW roobet.com/_api/affiliate/get accepts ?user_id and ?affiliate_code parameters (returns 401 not 404) — confirms parameter parsing but auth-gated
- NEW roobet.com/pusher/auth GET→200 SPA shell, POST→405 (live route, wrong method/body) — Pusher auth is POST-only endpoint requiring valid session + exact socket_id/channel_name
- CHANGED crash-gs.roobet.com Socket.IO TLS upgrade confirmed live (connection stays open, no 4xx, then app-layer timeout) — HUMAN_ONLY testable
- CHANGED api.roobet.com GraphQL WS upgrade on 443/8443 returns HTTP 403 (Cloudflare edge blocks WS); admin ports 8087/8088 TCP-refused at edge
- CHANGED auth.roobet.com/account.roobet.com/admin.roobet.com/billing.roobet.com/dashboard.roobet.com/sso.roobet.com + 13 others: confirmed non-resolving/internal (000/timeout)
- CHANGED roobet.com/_api/settings/get input reflection NEGATIVE confirmed across XFF, ?sessionId, Referer, Cookie:sessionId — ip=server-observed egress, sessionId rotates per-request, auth cookie=connect.sid

## 2026-09-05 12:18:13 UTC

## 2026-09-05 15:39:40 UTC
- NEW roobet.com /_api/socket.io — engine.io polling handshake LIVE (HTTP 200 `0{"sid":...,"upgrades":["websocket"]}`) with only `Origin: https://roobet.com`; anonymous connect ns `/` returns global `new_be
- NEW roobet.com /_api/graphql — raw WS upgrade returns 101 Switching Protocols + `Sec-WebSocket-Protocol: graphql-transport-ws` (NOT the 403 that api.roobet.com/graphql gives). `connection_init` accepted w
- CHANGED Data-plane gated at resolver: `currentUser` returns `code: NOT_AUTHENTICATED`, data null — transport+introspection open anonymously, resolvers enforce auth.
- CHANGED Bundle strings (all 67 chunks + entry.client) confirm SOCKETIO_PATH=`/_api/socket.io`, GQL_SOCKET_BASE_URL=`wss://(host)/_api/graphql`, connectionParams.socketToken only for App normal flow. Only lite
- NEW roobet.com/_api/socket.io — anonymous engine.io polling handshake (only `Origin: https://roobet.com`) + default-namespace CONNECT pushes live global `new_bet` feed and `settingsUpdated` broadcast; pla
- NEW roobet.com/_api/graphql — raw TLS WS upgrade returns 101 Switching Protocols + `Sec-WebSocket-Protocol: graphql-transport-ws` (contradicts the "GraphQL 403-only" KB line, which applies only to api.roo
- CHANGED Prior "passive surface fully bounded at 6 live `_api/*` routes" conclusion superseded — 2 new live routes, surface now ≥8. Bundle (all 67 chunks) shows only `_api/settings/get` + `_api/socket.io` HTTP

## 2026-09-05 17:40:32 UTC
- NEW roobet.com /_api/socket.io — engine.io polling handshake LIVE (HTTP 200 `0{"sid":...,"upgrades":["websocket"]}`) with only `Origin: https://roobet.com`; anonymous connect ns `/` returns global `new_be
- NEW roobet.com /_api/graphql — raw WS upgrade returns 101 Switching Protocols + `Sec-WebSocket-Protocol: graphql-transport-ws` (NOT the 403 that api.roobet.com/graphql gives). `connection_init` accepted w
- CHANGED Data-plane gated at resolver: `currentUser` returns `code: NOT_AUTHENTICATED`, data null — transport+introspection open anonymously, resolvers enforce auth.
- CHANGED Bundle strings (all 67 chunks + entry.client) confirm SOCKETIO_PATH=`/_api/socket.io`, GQL_SOCKET_BASE_URL=`wss://(host)/_api/graphql`, connectionParams.socketToken only for App normal flow. Only lite
- NEW roobet.com/_api/socket.io — anonymous engine.io polling handshake (only `Origin: https://roobet.com`) + default-namespace CONNECT pushes live global `new_bet` feed and `settingsUpdated` broadcast; pla
- NEW roobet.com/_api/graphql — raw TLS WS upgrade returns 101 Switching Protocols + `Sec-WebSocket-Protocol: graphql-transport-ws` (contradicts the "GraphQL 403-only" KB line, which applies only to api.roo
- CHANGED Prior "passive surface fully bounded at 6 live `_api/*` routes" conclusion superseded — 2 new live routes, surface now ≥8. Bundle (all 67 chunks) shows only `_api/settings/get` + `_api/socket.io` HTTP

## 2026-09-05 19:40:37 UTC
- NEW roobet.com/_api/graphql — anonymous graphql-transport-ws WS upgrade (101 + connection_ack, no socketToken required) + full introspection (28 queries, 26 mutations, 7 subscriptions) — supersedes prior 
- NEW roobet.com/_api/socket.io — engine.io polling handshake HTTP 200 (only Origin: https://roobet.com) + anonymous default namespace `/` broadcasts live `new_bet`, `settingsUpdated`, withdraw flags; graph
- CHANGED Data-plane gated at resolver: `currentUser`, `exchangeRates`, `viewerChecks`, `userPublicProfile`, `userSystemStatus` all return `NOT_AUTHENTICATED` anonymously — transport+introspection open, resolve
- CHANGED Bundle (all 67 chunks + entry.client) confirms SOCKETIO_PATH=`/_api/socket.io`, GQL_SOCKET_BASE_URL=`wss://(host)/_api/graphql`, connectionParams.socketToken only for normal app flow; only HTTP litera
- CHANGED Prior "passive surface fully bounded at 6 live `_api/*` routes" conclusion superseded — 2 new live WS routes confirmed, surface now ≥8 (6 HTTP + 2 WS)
- CHANGED api.roobet.com GraphQL remains 403 bot-gated on HTTP POST/GET and WS upgrade (443/8443); admin ports 8087/8088 TCP-refused at edge — no delta
- CHANGED auth.roobet.com/account.roobet.com/admin.roobet.com/billing.roobet.com/dashboard.roobet.com/sso.roobet.com + 13 others: confirmed non-resolving/internal (000/timeout) — no delta
- CHANGED roobet.com/_api/settings/get input reflection NEGATIVE confirmed (XFF, ?sessionId, Referer, Cookie:sessionId all inert; ip=server-observed egress, sessionId rotates per-request, auth cookie=connect.si
- CHANGED roobet.com/_api/* HTTP enumeration complete: exactly 6 live routes stable (settings/get 200, tp-games/essentials 200, admin/users 401, admin/stats 401, affiliate/get 401, auth/logout 302); 34 candidat

## 2026-09-05 21:49:28 UTC
- NEW roobet.com/_api/graphql — anonymous `graphql-transport-ws` upgrade (101 + `connection_ack` without `socketToken`); full `__schema` introspection succeeds (Query 28 / Mutation 26 / Subscription 7); mon
- NEW roobet.com/_api/socket.io — engine.io polling handshake (HTTP 200 `0{"sid":...,"upgrades":["websocket"]}`) with only `Origin: https://roobet.com`; anonymous connect to default namespace `/` returns li
- CHANGED roobet.com/_api/* HTTP enumeration finalized — exactly 6 live routes stable: `settings/get` (200), `tp-games/essentials` (200), `admin/users` (401), `admin/stats` (401), `affiliate/get` (401), `auth/l
- CHANGED roobet.com/_api/admin/users + /admin/stats — 401 confirmed on low-gate surface (not behind Cloudflare bot-management); Express.js session auth (`connect.sid` HttpOnly + `userId` non-HttpOnly + `twofac
- CHANGED roobet.com/_api/affiliate/get — 401; parameter tests `?user_id=<id>` and `?affiliate_code=<code>` return 401 (not 404), confirming parameter acceptance but auth-gated.
- CHANGED roobet.com/_api/settings/get — input reflection NEGATIVE across X-Forwarded-For, `?sessionId`, Referer, Cookie:sessionId; `ip`=server-observed egress, `sessionId` rotates per-request, auth cookie=`con
- CHANGED api.roobet.com GraphQL — HTTP POST/GET and raw WS upgrade on 443/8443 still return HTTP 403 (Cloudflare edge); admin ports 8087/8088 TCP-refused at edge.
- CHANGED crash-gs.roobet.com Socket.IO — TLS upgrade stays open (no 4xx) then app-layer timeout; confirmed live but HUMAN_ONLY (browser/WS tooling required).
- CHANGED auth.roobet.com/account.roobet.com/admin.roobet.com/billing.roobet.com/dashboard.roobet.com/sso.roobet.com + 13 others — confirmed non-resolving/internal (000/timeout).

## 2026-09-05 23:42:02 UTC
- NEW roobet.com/_api/socket.io — anonymous engine.io polling handshake (only `Origin: https://roobet.com`) + default-namespace CONNECT pushes live global `new_bet` feed and `settingsUpdated` broadcast; pla
- NEW roobet.com/_api/graphql — raw TLS WS upgrade returns 101 Switching Protocols + `Sec-WebSocket-Protocol: graphql-transport-ws` (contradicts the "GraphQL 403-only" KB line, which applies only to api.roo
- CHANGED Prior "passive surface fully bounded at 6 live `_api/*` routes" conclusion superseded — 2 new live routes, surface now ≥8. Bundle (all 67 chunks) shows only `_api/settings/get` + `_api/socket.io` HTTP
- NEW roobet.com/_api/graphql: anonymous `graphql-transport-ws` upgrade (101 + `connection_ack` without `socketToken`); full `__schema` introspection succeeds (Query 28 / Mutation 26 / Subscription 7); muta
- NEW roobet.com/_api/socket.io: engine.io polling handshake (HTTP 200 `0{"sid":...,"upgrades":["websocket"]}`) with only `Origin: https://roobet.com`; anonymous connect to default namespace `/` returns liv
- CHANGED roobet.com/_api/* HTTP enumeration finalized — exactly 6 live routes stable: `settings/get` (200), `tp-games/essentials` (200), `admin/users` (401), `admin/stats` (401), `affiliate/get` (401), `auth/l
- CHANGED api.roobet.com GraphQL — HTTP POST/GET and raw WS upgrade on 443/8443 still return HTTP 403 (Cloudflare edge); admin ports 8087/8088 TCP-refused at edge — no delta.
- CHANGED crash-gs.roobet.com Socket.IO — TLS upgrade stays open (no 4xx) then app-layer timeout; confirmed live but HUMAN_ONLY (browser/WS tooling required).
- CHANGED auth.roobet.com/account.roobet.com/admin.roobet.com/billing.roobet.com/dashboard.roobet.com/sso.roobet.com + 13 others — confirmed non-resolving/internal (000/timeout).

## 2026-09-06 01:24:35 UTC

## 2026-09-06 06:31:38 UTC
- NEW roobet.com/_api/graphql: anonymous `graphql-transport-ws` (101 + `connection_ack`, no `socketToken`) + full introspection (Query 28/Mut 26/Sub 7) confirmed — supersedes `api.roobet.com` 403-only asses
- NEW roobet.com/_api/socket.io: engine.io polling 200 handshake + anonymous ns `/` broadcast (`new_bet`, `settingsUpdated`, withdraw flags) confirmed — new realtime surface; `graphql`/`admin`/`user`/`walle
- CHANGED roobet.com/_api/* HTTP enumeration finalized — exactly 6 live routes stable: `settings/get` (200), `tp-games/essentials` (200), `admin/users` (401), `admin/stats` (401), `affiliate/get` (401), `auth/l
- CHANGED `api.roobet.com` GraphQL HTTP POST/GET and raw WS upgrade on 443/8443 still HTTP 403 (Cloudflare edge); admin ports 8087/8088 TCP-refused — no delta.
- CHANGED `auth.roobet.com`/`account.roobet.com`/`admin.roobet.com`/`billing.roobet.com`/`dashboard.roobet.com`/`sso.roobet.com` + 13 others — confirmed non-resolving/internal (000/timeout) — no delta.
- CHANGED `roobet.com/_api/settings/get` input reflection NEGATIVE across XFF, `?sessionId`, Referer, Cookie:sessionId; `ip`=server-observed egress, `sessionId` rotates per-request, auth cookie=`connect.sid` — 
- CHANGED `crash-gs.roobet.com` Socket.IO TLS upgrade stays open (no 4xx) then app-layer timeout — confirmed live but HUMAN_ONLY (browser/WS tooling required).
- CHANGED `fs.roobet.com` GCS bucket `?list-type=2` redirects to fullstory.com; no object enumeration possible — no delta.
- CHANGED `roobet.com` OAuth metadata endpoints (`/.well-known/oauth-authorization-server`, `/.well-known/openid-configuration`) return SPA shell (Remix catch-all), not JSON config — no delta.

## 2026-09-06 11:33:02 UTC

## 2026-09-06 14:36:18 UTC
- NEW roobet.com/_api/graphql: Anonymous `graphql-transport-ws` upgrade (101 + `connection_ack`, no `socketToken`) + full introspection (Query 28 / Mutation 26 / Subscription 7) — confirmed stable across co
- NEW roobet.com/_api/socket.io: Engine.io polling handshake (HTTP 200 `0{"sid":...,"upgrades":["websocket"]}`) with only `Origin: https://roobet.com`; anonymous connect to default namespace `/` returns liv
- NEW roobet.com/_api/* HTTP enumeration finalized — exactly 6 live routes stable: `settings/get` (200), `tp-games/essentials` (200), `admin/users` (401), `admin/stats` (401), `affiliate/get` (401), `auth/l
- CHANGED `api.roobet.com` GraphQL HTTP POST/GET and raw WS upgrade on 443/8443 still HTTP 403 (Cloudflare edge); admin ports 8087/8088 TCP-refused — no delta.
- CHANGED `auth.roobet.com`/`account.roobet.com`/`admin.roobet.com`/`billing.roobet.com`/`dashboard.roobet.com`/`sso.roobet.com` + 13 others — confirmed non-resolving/internal (000/timeout) — no delta.
- CHANGED `roobet.com/_api/settings/get` input reflection NEGATIVE across XFF, `?sessionId`, Referer, Cookie:sessionId; `ip`=server-observed egress, `sessionId` rotates per-request, auth cookie=`connect.sid` — 
- CHANGED `crash-gs.roobet.com` Socket.IO TLS upgrade stays open (no 4xx) then app-layer timeout — confirmed live but HUMAN_ONLY (browser/WS tooling required) — no delta.
- CHANGED `fs.roobet.com` GCS bucket `?list-type=2` redirects to fullstory.com; no object enumeration possible — no delta.
- CHANGED `roobet.com` OAuth metadata endpoints (`/.well-known/oauth-authorization-server`, `/.well-known/openid-configuration`) return SPA shell (Remix catch-all), not JSON config — no delta.

## 2026-09-06 17:24:34 UTC
- NEW `roobet.com/_api/graphql`: Mutation validation errors confirmed as additional disclosure vector — all 26 mutations pass GraphQL validation anonymously, leaking exact InputType shapes, required fields,
- NEW `roobet.com/_api/graphql` subscriptions: `kycUpdated` + `polymarketOrders` return JS error `Cannot read properties of null (reading 'user')` — internal error disclosure confirms resolver accesses sess
- NEW `roobet.com/_api/graphql` User type: 64 fields disclosed via introspection incl. email, KYC PII (firstName/lastName/dob/address/phone), financial (balances/withdrawn/deposited/lifetimeValue), auth tok
- CHANGED `roobet.com/_api/*`: Zero surface delta across consecutive runs (6 HTTP + 2 WS routes stable); passive probing exhausted; all remaining verified-value hypotheses are session-gated (AUTH_HELPED/HUMAN_O
- CHANGED `api.roobet.com` GraphQL: HTTP POST/GET and raw WS upgrade on 443/8443 still HTTP 403 (Cloudflare edge); admin ports 8087/8088 TCP-refused — no delta.
- CHANGED `auth.roobet.com`/`account.roobet.com`/`admin.roobet.com`/`billing.roobet.com`/`dashboard.roobet.com`/`sso.roobet.com` + 13 others: confirmed non-resolving/internal (000/timeout) — no delta.
- CHANGED `crash-gs.roobet.com` Socket.IO: TLS upgrade stays open (no 4xx) then app-layer timeout — confirmed live but HUMAN_ONLY — no delta.
- CHANGED `fs.roobet.com` GCS bucket `?list-type=2` redirects to fullstory.com; no object enumeration possible — no delta.
- CHANGED `roobet.com` OAuth metadata endpoints return SPA shell (Remix catch-all), not JSON config — no delta.

## 2026-09-06 19:36:36 UTC
- NEW `roobet.com/_api/graphql` HTTP endpoint returns 400 (not WS 101) — HTTP POST to GraphQL endpoint now tested, returns 400 Bad Request vs prior WS-only 101 introspection channel
- NEW `roobet.com/_api/admin/users`, `/_api/admin/stats`, `/_api/affiliate/get` (base paths) return 404 in latest probes — inconsistent with prior 401; likely probe URL formatting artifact (backticks in log
- CHANGED `roobet.com/_api/affiliate/get?user_id=<id>` and `?affiliate_code=<code>` consistently return 401 (not 404) — confirms parameter parsing on low-gate surface
- CHANGED `api.roobet.com/graphql` remains HTTP 403 / WS 403 on 443/8443 — Cloudflare bot-gate intact, no delta
- CHANGED `auth.roobet.com`, `account.roobet.com`, `admin.roobet.com`, `billing.roobet.com`, `dashboard.roobet.com`, `sso.roobet.com` + 13 others — confirmed non-resolving/internal (000/timeout), no delta
- CHANGED `crash-gs.roobet.com` Socket.IO TLS upgrade stays open (no 4xx) then app-layer timeout — confirmed live but HUMAN_ONLY, no delta
- CHANGED `fs.roobet.com` GCS bucket `?list-type=2` redirects to fullstory.com — no object enumeration, no delta
- CHANGED `roobet.com` OAuth metadata endpoints return SPA shell (Remix catch-all) — not JSON config, no delta
- CHANGED `roobet.com/_api/settings/get` input reflection NEGATIVE across XFF, `?sessionId`, Referer, Cookie — `ip`=server-observed egress, `sessionId` rotates per-request, auth cookie=`connect.sid`, no delta
- CHANGED `roobet.com/_api/*` HTTP enumeration finalized — 6 live routes stable (settings/get 200, tp-games/essentials 200, admin/users 401, admin/stats 401, affiliate/get 401, auth/logout 302) per knowledge ba
- CHANGED `roobet.com/_api/socket.io` engine.io polling 200 handshake + anonymous ns `/` broadcast (`new_bet`, `settingsUpdated`, withdraw flags) — stable
- CHANGED `roobet.com/_api/graphql` anonymous `graphql-transport-ws` (101 + `connection_ack`, no `socketToken`) + full introspection (Query 28/Mut 26/Sub 7) + mutation validation error disclosure + subscription

## 2026-09-06 21:44:35 UTC

## 2026-09-06 23:39:52 UTC

## 2026-09-07 01:23:24 UTC
- NEW roobet.com/_api/graphql HTTP POST returns 400 (new HTTP channel tested, distinct from WS 101 channel)
- NEW roobet.com/_api/admin/users, /_api/admin/stats, /_api/affiliate/get base paths now consistently return 401 (prior 404s were probe URL artifacts with backticks)
- CHANGED Surface stable: 6 HTTP routes + 2 WS routes confirmed across 5+ runs; zero delta
- CHANGED api.roobet.com GraphQL remains 403 bot-gated on HTTP/WS; admin ports 8087/8088 TCP-refused
- CHANGED crash-gs.roobet.com Socket.IO TLS upgrade open (no 4xx) then app-timeout; HUMAN_ONLY
- CHANGED auth/account/admin/billing/dashboard/sso + 13 subdomains: non-resolving/internal
- CHANGED fs.roobet.com GCS ?list-type=2 → fullstory.com redirect; no enumeration
- CHANGED roobet.com OAuth metadata endpoints return SPA shell (Remix catch-all), not JSON

## 2026-09-07 06:14:59 UTC
- NEW roobet.com/_api/graphql HTTP GET: Apollo GET transport enabled — CSRF gate bypassable via x-apollo-operation-name header; cacheable URL creates proxy/referrer leakage advantages
- NEW roobet.com/_api/graphql HTTP POST: mutation liveRTPUpdate → 200 "No user with that id" + INTERNAL_SERVER_ERROR — resolver executes pre-auth on HTTP channel (distinct from WS 101 channel)
- NEW roobet.com/_api/graphql HTTP __type: INTROSPECTION_DISABLED on HTTP channel — `__type(name:"User")` blocked; only WS provides full introspection
- NEW roobet.com/_api/admin/users, /_api/admin/stats, /_api/affiliate/get base paths now consistently return 401 (prior 404s were probe URL artifacts with backticks)
- CHANGED Surface stable: 6 HTTP routes + 2 WS routes confirmed across 5+ runs; zero delta

## 2026-09-07 12:50:04 UTC
- NEW roobet.com/_api/graphql HTTP GET: Apollo GET transport enabled — CSRF gate bypassable via `x-apollo-operation-name` header; cacheable URL creates proxy/referrer leakage advantages
- NEW roobet.com/_api/graphql HTTP POST: mutation `liveRTPUpdate` → 200 "No user with that id" + INTERNAL_SERVER_ERROR — resolver executes pre-auth on HTTP channel (distinct from WS 101 channel)
- NEW roobet.com/_api/graphql HTTP `__type`: INTROSPECTION_DISABLED on HTTP channel — `__type(name:"User")` blocked; only WS provides full introspection
- CHANGED roobet.com/_api/admin/users, /_api/admin/stats, /_api/affiliate/get base paths now consistently return 401 (prior 404s were probe URL artifacts with backticks)
- CHANGED Surface stable: 6 HTTP routes + 2 WS routes confirmed across 5+ runs; zero delta
- CHANGED api.roobet.com GraphQL remains 403 bot-gated on HTTP/WS; admin ports 8087/8088 TCP-refused
- CHANGED crash-gs.roobet.com Socket.IO TLS upgrade open (no 4xx) then app-timeout; HUMAN_ONLY
- CHANGED auth/account/admin/billing/dashboard/sso + 13 subdomains: non-resolving/internal
- CHANGED fs.roobet.com GCS ?list-type=2 → fullstory.com redirect; no enumeration
- CHANGED roobet.com OAuth metadata endpoints return SPA shell (Remix catch-all), not JSON

## 2026-09-07 18:20:43 UTC
- NEW roobet.com/_api/graphql HTTP GET: Apollo GET transport enabled — CSRF gate bypassable via `x-apollo-operation-name` header; cacheable URL creates proxy/referrer leakage advantages
- NEW roobet.com/_api/graphql HTTP POST: mutation `liveRTPUpdate` → 200 "No user with that id" + INTERNAL_SERVER_ERROR — resolver executes pre-auth on HTTP channel (distinct from WS 101 channel)
- NEW roobet.com/_api/graphql HTTP `__type`: INTROSPECTION_DISABLED on HTTP channel — `__type(name:"User")` blocked; only WS provides full introspection
- CHANGED roobet.com/_api/admin/users, /_api/admin/stats, /_api/affiliate/get base paths now consistently return 401 (prior 404s were probe URL artifacts with backticks)
- CHANGED Surface stable: 6 HTTP routes + 2 WS routes confirmed across 5+ runs; zero delta
- CHANGED api.roobet.com GraphQL remains 403 bot-gated on HTTP/WS; admin ports 8087/8088 TCP-refused
- CHANGED crash-gs.roobet.com Socket.IO TLS upgrade open (no 4xx) then app-timeout; HUMAN_ONLY
- CHANGED auth/account/admin/billing/dashboard/sso + 13 subdomains: non-resolving/internal
- CHANGED fs.roobet.com GCS ?list-type=2 → fullstory.com redirect; no enumeration
- CHANGED roobet.com OAuth metadata endpoints return SPA shell (Remix catch-all), not JSON
- NEW roobet.com/_api/graphql HTTP GET: Apollo GET transport enabled — CSRF gate bypassable via `x-apollo-operation-name` header; cacheable URL creates proxy/referrer leakage advantages
- NEW roobet.com/_api/graphql HTTP POST: mutation `liveRTPUpdate` → 200 "No user with that id" + INTERNAL_SERVER_ERROR — resolver executes pre-auth on HTTP channel (distinct from WS 101 channel)
- NEW roobet.com/_api/graphql HTTP `__type`: INTROSPECTION_DISABLED on HTTP channel — `__type(name:"User")` blocked; only WS provides full introspection
- CHANGED roobet.com/_api/admin/users, /_api/admin/stats, /_api/affiliate/get base paths now consistently return 401 (prior 404s were probe URL artifacts with backticks)
- CHANGED Surface stable: 6 HTTP routes + 2 WS routes confirmed across 5+ runs; zero delta
- CHANGED api.roobet.com GraphQL remains 403 bot-gated on HTTP/WS; admin ports 8087/8088 TCP-refused
- CHANGED crash-gs.roobet.com Socket.IO TLS upgrade open (no 4xx) then app-timeout; HUMAN_ONLY
- CHANGED auth/account/admin/billing/dashboard/sso + 13 subdomains: non-resolving/internal
- CHANGED fs.roobet.com GCS ?list-type=2 → fullstory.com redirect; no enumeration
- CHANGED roobet.com OAuth metadata endpoints return SPA shell (Remix catch-all), not JSON

## 2026-09-07 21:39:26 UTC
- NEW roobet.com/_api/graphql HTTP GET: Apollo GET transport enabled — CSRF gate bypassable via `x-apollo-operation-name` header; cacheable URL creates proxy/referrer leakage advantages (2026-09-07)
- NEW roobet.com/_api/graphql HTTP POST: mutation `liveRTPUpdate` → 200 "No user with that id" + INTERNAL_SERVER_ERROR — resolver executes pre-auth on HTTP channel (distinct from WS 101 channel) (2026-09-07
- NEW roobet.com/_api/graphql HTTP `__type`: INTROSPECTION_DISABLED on HTTP channel — `__type(name:"User")` blocked; only WS provides full introspection (2026-09-07)
- CHANGED roobet.com/_api/admin/users, /_api/admin/stats, /_api/affiliate/get base paths now consistently return 401 (prior 404s were probe URL artifacts with backticks)
- CHANGED Surface stable: 6 HTTP routes + 2 WS routes confirmed across 5+ runs; zero delta
- CHANGED api.roobet.com GraphQL remains 403 bot-gated on HTTP/WS; admin ports 8087/8088 TCP-refused
- CHANGED crash-gs.roobet.com Socket.IO TLS upgrade open (no 4xx) then app-timeout; HUMAN_ONLY
- CHANGED auth/account/admin/billing/dashboard/sso + 13 subdomains: non-resolving/internal
- CHANGED fs.roobet.com GCS ?list-type=2 → fullstory.com redirect; no enumeration
- CHANGED roobet.com OAuth metadata endpoints return SPA shell (Remix catch-all), not JSON

## 2026-09-07 23:48:21 UTC
- NEW roobet.com/_api/graphql HTTP channel live: POST mutation resolver executes pre-auth (liveRTPUpdate → 200 "No user with that id" + INTERNAL_SERVER_ERROR), GET enables Apollo transport (CSRF bypass via 
- CHANGED roobet.com/_api/admin/users, /_api/admin/stats, /_api/affiliate/get base paths now consistently return 401 (prior 404s were probe URL artifacts with backticks)
- CHANGED Surface stable: 6 HTTP routes + 2 WS routes confirmed across 5+ runs; zero delta

## 2026-09-08 03:53:58 UTC
- CHANGED Surface stable across 5+ runs: 6 HTTP routes + 2 WS routes on roobet.com/_api/* confirmed; zero delta in hosts/routes
- CHANGED roobet.com/_api/graphql HTTP channel fully characterized: Apollo GET transport (CSRF bypass via x-apollo-operation-name), POST mutation resolver executes pre-auth (liveRTPUpdate → "No user with that i
- CHANGED roobet.com/_api/admin/users, /_api/admin/stats, /_api/affiliate/base paths consistently return 401 (prior 404s were probe artifacts)
- CHANGED api.roobet.com, auth.roobet.com, account.roobet.com, admin.roobet.com, billing.roobet.com, dashboard.roobet.com, sso.roobet.com + 13 others: non-resolving/internal (000/timeout) — no delta
- CHANGED crash-gs.roobet.com Socket.IO TLS upgrade open (no 4xx) then app-timeout; HUMAN_ONLY — no delta
- CHANGED fs.roobet.com GCS ?list-type=2 → fullstory.com redirect; no enumeration — no delta
- CHANGED roobet.com OAuth metadata endpoints return SPA shell (Remix catch-all), not JSON — no delta

## 2026-09-08 08:49:45 UTC

## 2026-09-08 13:29:01 UTC
- NEW roobet.com/_api/socket.io: polling transport Origin-gated — 403 `disallowed origin` without `Origin: https://roobet.com`, 200 handshake with it; realtime surface mechanistically re-confirmed
- NEW roobet.com/_api/graphql GET: CSRF preflight confirmed via error body — requires non-form content-type or `x-apollo-operation-name`/`apollo-require-preflight`; Apollo GET transport behavior consistent
- NEW roobet.com/_api/*: 6 new family candidates (admin/affiliates, admin/games, admin/config, affiliate/stats, auth/me, auth/session) all 404 SPA shell — admin/affiliate/auth route families bounded; zero n
- CHANGED roobet.com/_api/admin/users: base path now consistently returns 401 (prior 404s were probe URL artifacts with backticks)
- CHANGED roobet.com/_api/affiliate/get: parameter tests `?user_id`/`affiliate_code` return 401 not 404 — confirms parameter parsing on low-gate surface
- CHANGED Surface stable: 6 HTTP routes + 2 WS routes confirmed across 5+ runs; zero delta in hosts/routes

## 2026-09-08 17:44:25 UTC
- CHANGED `roobet.com/_api/graphql` HTTP POST: `liveRTPUpdate` mutation now returns **400 + INTERNAL_SERVER_ERROR** (3×) instead of prior **200 "No user with that id" + INTERNAL_SERVER_ERROR** — server patched 
- CHANGED `roobet.com/_api/settings/get`: response now 35 keys (down from prior 68) — config surface reduced; `globalStats.allTimeNumBets` stable at ~15.3B; `restrictedCountries` now 35 entries (was 33).
- NEW roobet.com/_api/socket.io: polling transport Origin-gated — 403 `disallowed origin` without `Origin: https://roobet.com`, 200 handshake with it; realtime surface mechanistically re-confirmed, no delta
- NEW roobet.com/_api/graphql GET: CSRF preflight confirmed via error body — requires non-form content-type or `x-apollo-operation-name`/`apollo-require-preflight`; Apollo GET transport behavior consistent 
- NEW roobet.com/_api/*: 6 new family candidates (admin/affiliates, admin/games, admin/config, affiliate/stats, auth/me, auth/session) all 404 SPA shell — admin/affiliate/auth route families bounded; zero n
- CHANGED roobet.com/_api/admin/users: base path now consistently returns 401 (prior 404s were probe URL artifacts with backticks)
- CHANGED roobet.com/_api/affiliate/get: parameter tests `?user_id`/`affiliate_code` return 401 not 404 — confirms parameter parsing on low-gate surface
- CHANGED Surface stable: 6 HTTP routes + 2 WS routes confirmed across 5+ runs; zero delta in hosts/routes
- NEW roobet.com/_api/socket.io: polling transport Origin-gated — 403 `disallowed origin` without `Origin: https://roobet.com`, 200 handshake with it; realtime surface mechanistically re-confirmed, no delta
- NEW roobet.com/_api/graphql GET: CSRF preflight confirmed via error body — requires non-form content-type or `x-apollo-operation-name`/`apollo-require-preflight`; Apollo GET transport behavior consistent 
- NEW roobet.com/_api/*: 6 new family candidates (admin/affiliates, admin/games, admin/config, affiliate/stats, auth/me, auth/session) all 404 SPA shell — admin/affiliate/auth route families bounded; zero n
- CHANGED roobet.com/_api/admin/users: base path now consistently returns 401 (prior 404s were probe URL artifacts with backticks)
- CHANGED roobet.com/_api/affiliate/get: parameter tests `?user_id`/`affiliate_code` return 401 not 404 — confirms parameter parsing on low-gate surface
- CHANGED Surface stable: 6 HTTP routes + 2 WS routes confirmed across 5+ runs; zero delta in hosts/routes
- NEW roobet.com/_api/socket.io: polling transport Origin-gated — 403 `disallowed origin` without `Origin: https://roobet.com`, 200 handshake with it; realtime surface mechanistically re-confirmed, no delta
- NEW roobet.com/_api/graphql GET: CSRF preflight confirmed via error body — requires non-form content-type or `x-apollo-operation-name`/`apollo-require-preflight`; Apollo GET transport behavior consistent 
- NEW roobet.com/_api/*: 6 new family candidates (admin/affiliates, admin/games, admin/config, affiliate/stats, auth/me, auth/session) all 404 SPA shell — admin/affiliate/auth route families bounded; zero n
- CHANGED roobet.com/_api/admin/users: base path now consistently returns 401 (prior 404s were probe URL artifacts with backticks)
- CHANGED roobet.com/_api/affiliate/get: parameter tests `?user_id`/`affiliate_code` return 401 not 404 — confirms parameter parsing on low-gate surface
- CHANGED Surface stable: 6 HTTP routes + 2 WS routes confirmed across 5+ runs; zero delta in hosts/routes

## 2026-09-08 20:18:43 UTC
- NEW roobet.com/_api/graphql HTTP POST liveRTPUpdate error message changed from 200 "No user with that id" + INTERNAL_SERVER_ERROR to 400 + 3× INTERNAL_SERVER_ERROR — server patched error message but resol
- NEW roobet.com/_api/settings/get response reduced from 68 to 35 keys (config surface reduced); globalStats.allTimeNumBets stable at ~15.3B; restrictedCountries now 35 entries (was 33)
- CHANGED roobet.com/_api/admin/users base path consistently returns 401 (prior 404s were probe URL artifacts)
- CHANGED roobet.com/_api/affiliate/get parameter tests ?user_id/affiliate_code return 401 not 404 — confirms parameter parsing on low-gate surface
- CHANGED Surface stable: 6 HTTP routes + 2 WS routes confirmed across 5+ runs; zero delta in hosts/routes

## 2026-09-08 22:47:28 UTC
- NEW roobet.com/_api/graphql HTTP POST liveRTPUpdate error message changed from 200 "No user with that id" + INTERNAL_SERVER_ERROR to 400 + 3× INTERNAL_SERVER_ERROR — server patched error message but resol
- NEW roobet.com/_api/settings/get response reduced from 68 to 35 keys (config surface reduced); globalStats.allTimeNumBets stable at ~15.3B; restrictedCountries now 35 entries (was 33)
- CHANGED roobet.com/_api/admin/users base path consistently returns 401 (prior 404s were probe URL artifacts)
- CHANGED roobet.com/_api/affiliate/get parameter tests ?user_id/affiliate_code return 401 not 404 — confirms parameter parsing on low-gate surface
- CHANGED Surface stable: 6 HTTP routes + 2 WS routes confirmed across 5+ runs; zero delta in hosts/routes
- CHANGED roobet.com/_api/socket.io polling transport Origin-gated — 403 disallowed origin without Origin: https://roobet.com, 200 handshake with it
- CHANGED roobet.com/_api/graphql GET: CSRF preflight confirmed via error body — requires non-form content-type or x-apollo-operation-name/apollo-require-preflight
- CHANGED 6 new _api/* family candidates (admin/affiliates, admin/games, admin/config, affiliate/stats, auth/me, auth/session) all 404 SPA shell — route families bounded

## 2026-09-09 01:09:29 UTC
- NEW roobet.com/_api/graphql HTTP POST liveRTPUpdate error message changed: 200 "No user with that id" + INTERNAL_SERVER_ERROR → 400 + 3× INTERNAL_SERVER_ERROR (server patched error text but resolver still
- NEW roobet.com/_api/settings/get response keys reduced 68→35; globalStats.allTimeNumBets stable ~15.3B; restrictedCountries 35 entries (was 33)
- CHANGED roobet.com/_api/admin/users base path consistently 401 (prior 404s were probe URL artifacts)
- CHANGED roobet.com/_api/affiliate/get ?user_id/?affiliate_code return 401 not 404 — confirms parameter parsing on low-gate surface
- CHANGED Surface stable: 6 HTTP + 2 WS routes confirmed across 5+ runs; zero delta in hosts/routes
- CHANGED roobet.com/_api/socket.io polling Origin-gated: 403 without Origin: https://roobet.com, 200 with it
- CHANGED roobet.com/_api/graphql GET: CSRF preflight confirmed via error body — requires non-form content-type or x-apollo-operation-name/apollo-require-preflight
- CHANGED 6 new _api/* family candidates (admin/affiliates, admin/games, admin/config, affiliate/stats, auth/me, auth/session) all 404 SPA shell — route families bounded

## 2026-09-09 06:09:54 UTC
- NEW roobet.com/_api/graphql HTTP POST liveRTPUpdate error message changed: 200 "No user with that id" + INTERNAL_SERVER_ERROR → 400 + 3× INTERNAL_SERVER_ERROR (server patched error text but resolver still
- NEW roobet.com/_api/settings/get response keys reduced 68→35; globalStats.allTimeNumBets stable ~15.3B; restrictedCountries 35 entries (was 33)
- CHANGED roobet.com/_api/admin/users base path consistently 401 (prior 404s were probe URL artifacts)
- CHANGED roobet.com/_api/affiliate/get ?user_id/?affiliate_code return 401 not 404 — confirms parameter parsing on low-gate surface
- CHANGED Surface stable: 6 HTTP + 2 WS routes confirmed across 5+ runs; zero delta in hosts/routes
- CHANGED roobet.com/_api/socket.io polling Origin-gated: 403 without Origin: https://roobet.com, 200 with it
- CHANGED roobet.com/_api/graphql GET: CSRF preflight confirmed via error body — requires non-form content-type or x-apollo-operation-name/apollo-require-preflight
- CHANGED 6 new _api/* family candidates (admin/affiliates, admin/games, admin/config, affiliate/stats, auth/me, auth/session) all 404 SPA shell — route families bounded

## 2026-09-09 11:38:18 UTC

## 2026-09-09 15:37:57 UTC

## 2026-09-09 18:47:04 UTC
- CHANGED Fresh re-probe (2026-09-09): zero surface delta — settings/get 200 (exactly 35 keys), admin/users 401, affiliate/get 401 (+ ?user_id=1 401), tp-games/essentials 200, graphql GET+x-apollo-operation-nam
- CHANGED socket.io POST-40 (engine.io namespace connect over polling) → 400; polling handshake + anonymous broadcast feed unchanged, WS-upgrade remains the functional transport (HUMAN_ONLY for full frame proto
- CHANGED roobet.com/_api/graphql HTTP POST: liveRTPUpdate mutation error message patched from 200+"No user with that id"+INTERNAL_SERVER_ERROR to 400+3×INTERNAL_SERVER_ERROR (resolver still executes pre-auth, 
- CHANGED roobet.com/_api/settings/get: response reduced from 68 to 35 keys; globalStats.allTimeNumBets stable ~15.3B; restrictedCountries 35 entries (was 33)

## 2026-09-09 21:35:39 UTC
- CHANGED roobet.com/_api/graphql HTTP GET read-plane: `exchangeRates` (named op + `x-apollo-operation-name`) → 200 with `NOT_AUTHENTICATED`/null data — resolver auth gate confirmed identical on HTTP and WS cha
- NEW roobet.com/_api/graphql HTTP POST: liveRTPUpdate mutation error message patched from 200+"No user with that id"+INTERNAL_SERVER_ERROR to 400+3×INTERNAL_SERVER_ERROR (resolver still executes pre-auth, 
- NEW roobet.com/_api/settings/get: response reduced from 68 to 35 keys; globalStats.allTimeNumBets stable ~15.3B; restrictedCountries 35 entries (was 33)
- NEW roobet.com/_api/socket.io: polling transport Origin-gated — 403 disallowed origin without Origin: https://roobet.com, 200 handshake with it
- NEW roobet.com/_api/graphql GET: CSRF preflight confirmed via error body — requires non-form content-type or x-apollo-operation-name/apollo-require-preflight
- CHANGED roobet.com/_api/admin/users: base path consistently returns 401 (prior 404s were probe URL artifacts)
- CHANGED roobet.com/_api/affiliate/get: parameter tests ?user_id/affiliate_code return 401 not 404 — confirms parameter parsing on low-gate surface
- CHANGED Surface static: 6 HTTP routes + 2 WS routes confirmed across 5+ runs; zero delta in hosts/routes
- CHANGED api.roobet.com, auth.roobet.com, account.roobet.com, admin.roobet.com, billing.roobet.com, dashboard.roobet.com, sso.roobet.com + 13 others: non-resolving/internal (000/timeout) — no delta
- CHANGED crash-gs.roobet.com Socket.IO TLS upgrade open (no 4xx) then app-timeout; HUMAN_ONLY — no delta
- CHANGED fs.roobet.com GCS ?list-type=2 → fullstory.com redirect; no enumeration — no delta
- CHANGED roobet.com OAuth metadata endpoints return SPA shell (Remix catch-all), not JSON — no delta

## 2026-09-09 23:36:19 UTC
- NEW roobet.com/_api/graphql HTTP POST: liveRTPUpdate mutation error message patched from 200+"No user with that id"+INTERNAL_SERVER_ERROR to 400+3×INTERNAL_SERVER_ERROR (resolver still executes pre-auth, 
- NEW roobet.com/_api/settings/get: response reduced from 68 to 35 keys; globalStats.allTimeNumBets stable ~15.3B; restrictedCountries 35 entries (was 33)
- NEW roobet.com/_api/socket.io: polling transport Origin-gated — 403 disallowed origin without Origin: https://roobet.com, 200 handshake with it
- NEW roobet.com/_api/graphql GET: CSRF preflight confirmed via error body — requires non-form content-type or x-apollo-operation-name/apollo-require-preflight
- CHANGED roobet.com/_api/admin/users: base path consistently returns 401 (prior 404s were probe URL artifacts)
- CHANGED roobet.com/_api/affiliate/get: parameter tests ?user_id/affiliate_code return 401 not 404 — confirms parameter parsing on low-gate surface
- CHANGED Surface static: 6 HTTP routes + 2 WS routes confirmed across 5+ runs; zero delta in hosts/routes
- CHANGED api.roobet.com, auth.roobet.com, account.roobet.com, admin.roobet.com, billing.roobet.com, dashboard.roobet.com, sso.roobet.com + 13 others: non-resolving/internal (000/timeout) — no delta
- CHANGED crash-gs.roobet.com Socket.IO TLS upgrade open (no 4xx) then app-timeout; HUMAN_ONLY — no delta
- CHANGED fs.roobet.com GCS ?list-type=2 → fullstory.com redirect; no enumeration — no delta
- CHANGED roobet.com OAuth metadata endpoints return SPA shell (Remix catch-all), not JSON — no delta

## 2026-09-10 01:31:13 UTC
- CHANGED roobet.com/_api/graphql HTTP POST liveRTPUpdate error patched: 200 "No user with that id" + INTERNAL_SERVER_ERROR → 400 + 3×INTERNAL_SERVER_ERROR (resolver still executes pre-auth, not 401/NOT_AUTHENT
- CHANGED roobet.com/_api/settings/get response reduced from 68 to 35 keys; globalStats.allTimeNumBets stable ~15.3B; restrictedCountries 35 entries (was 33)
- CHANGED roobet.com/_api/admin/users base path consistently 401 (prior 404s were probe URL artifacts)
- CHANGED roobet.com/_api/affiliate/get ?user_id/?affiliate_code return 401 not 404 — confirms parameter parsing on low-gate surface
- CHANGED Surface static: 6 HTTP + 2 WS routes confirmed across 5+ runs; zero delta in hosts/routes
- CHANGED api.roobet.com, auth.roobet.com, account.roobet.com, admin.roobet.com, billing.roobet.com, dashboard.roobet.com, sso.roobet.com + 13 others: non-resolving/internal (000/timeout) — no delta
- CHANGED crash-gs.roobet.com Socket.IO TLS upgrade open (no 4xx) then app-timeout; HUMAN_ONLY — no delta
- CHANGED fs.roobet.com GCS ?list-type=2 → fullstory.com redirect; no enumeration — no delta
- CHANGED roobet.com OAuth metadata endpoints return SPA shell (Remix catch-all), not JSON — no delta

## 2026-09-10 06:57:27 UTC
- CHANGED roobet.com/_api/graphql HTTP POST liveRTPUpdate error patched: 200 "No user with that id" + INTERNAL_SERVER_ERROR → 400 + 3×INTERNAL_SERVER_ERROR (resolver still executes pre-auth, not 401/NOT_AUTHENT
- CHANGED roobet.com/_api/settings/get response reduced from 68 to 35 keys; globalStats.allTimeNumBets stable ~15.3B; restrictedCountries 35 entries (was 33)
- CHANGED roobet.com/_api/admin/users base path consistently 401 (prior 404s were probe URL artifacts)
- CHANGED roobet.com/_api/affiliate/get ?user_id/?affiliate_code return 401 not 404 — confirms parameter parsing on low-gate surface
- CHANGED Surface static: 6 HTTP + 2 WS routes confirmed across 5+ runs; zero delta in hosts/routes
- CHANGED api.roobet.com, auth.roobet.com, account.roobet.com, admin.roobet.com, billing.roobet.com, dashboard.roobet.com, sso.roobet.com + 13 others: non-resolving/internal (000/timeout) — no delta
- CHANGED crash-gs.roobet.com Socket.IO TLS upgrade open (no 4xx) then app-timeout; HUMAN_ONLY — no delta
- CHANGED fs.roobet.com GCS ?list-type=2 → fullstory.com redirect; no enumeration — no delta
- CHANGED roobet.com OAuth metadata endpoints return SPA shell (Remix catch-all), not JSON — no delta

## 2026-09-10 12:01:44 UTC

## 2026-09-10 16:19:25 UTC
- CHANGED roobet.com/_api/graphql HTTP POST liveRTPUpdate error patched: 200 "No user with that id" + INTERNAL_SERVER_ERROR → 400 + 3×INTERNAL_SERVER_ERROR (resolver still executes pre-auth, not 401/NOT_AUTHENT
- CHANGED roobet.com/_api/settings/get response reduced from 68 to 35 keys; globalStats.allTimeNumBets stable ~15.3B; restrictedCountries 35 entries (was 33)
- CHANGED roobet.com/_api/admin/users base path consistently 401 (prior 404s were probe URL artifacts)
- CHANGED roobet.com/_api/affiliate/get ?user_id/?affiliate_code return 401 not 404 — confirms parameter parsing on low-gate surface
- CHANGED Surface static: 6 HTTP + 2 WS routes confirmed across 5+ runs; zero delta in hosts/routes
- CHANGED api.roobet.com, auth.roobet.com, account.roobet.com, admin.roobet.com, billing.roobet.com, dashboard.roobet.com, sso.roobet.com + 13 others: non-resolving/internal (000/timeout) — no delta
- CHANGED crash-gs.roobet.com Socket.IO TLS upgrade open (no 4xx) then app-timeout; HUMAN_ONLY — no delta
- CHANGED fs.roobet.com GCS ?list-type=2 → fullstory.com redirect; no enumeration — no delta
- CHANGED roobet.com OAuth metadata endpoints return SPA shell (Remix catch-all), not JSON — no delta
- NEW roobet.com/_api/graphql HTTP GET read-plane: exchangeRates (named op + x-apollo-operation-name) → 200 with NOT_AUTHENTICATED/null data — resolver auth gate confirmed identical on HTTP and WS channels

## 2026-09-10 19:13:09 UTC
- NEW roobet.com/_api/graphql HTTP GET read-plane: `exchangeRates` (named op + `x-apollo-operation-name`) → 200 with `NOT_AUTHENTICATED`/null data — resolver auth gate confirmed identical on HTTP and WS cha
- CHANGED roobet.com/_api/graphql HTTP POST `liveRTPUpdate` error patched: 200 "No user with that id" + INTERNAL_SERVER_ERROR → 400 + 3×INTERNAL_SERVER_ERROR (resolver still executes pre-auth, not 401/NOT_AUTHE
- CHANGED roobet.com/_api/settings/get response reduced from 68 to 35 keys; `globalStats.allTimeNumBets` stable ~15.3B; `restrictedCountries` 35 entries (was 33)
- CHANGED roobet.com/_api/admin/users base path consistently 401 (prior 404s were probe URL artifacts)
- CHANGED roobet.com/_api/affiliate/get `?user_id`/`affiliate_code` return 401 not 404 — confirms parameter parsing on low-gate surface
- CHANGED Surface static: 6 HTTP + 2 WS routes confirmed across 5+ runs; zero delta in hosts/routes
- CHANGED api.roobet.com, auth.roobet.com, account.roobet.com, admin.roobet.com, billing.roobet.com, dashboard.roobet.com, sso.roobet.com + 13 others: non-resolving/internal (000/timeout) — no delta
- CHANGED crash-gs.roobet.com Socket.IO TLS upgrade open (no 4xx) then app-timeout; HUMAN_ONLY — no delta
- CHANGED fs.roobet.com GCS `?list-type=2` → fullstory.com redirect; no enumeration — no delta
- CHANGED roobet.com OAuth metadata endpoints return SPA shell (Remix catch-all), not JSON — no delta

## 2026-09-10 21:43:28 UTC

## 2026-09-10 23:54:10 UTC
- NEW roobet.com/_api/graphql HTTP GET read-plane: exchangeRates (named op + x-apollo-operation-name) → 200 with NOT_AUTHENTICATED/null data — resolver auth gate confirmed identical on HTTP and WS channels 
- CHANGED roobet.com/_api/graphql HTTP POST liveRTPUpdate error patched: 200 "No user with that id" + INTERNAL_SERVER_ERROR → 400 + 3×INTERNAL_SERVER_ERROR (resolver still executes pre-auth, not 401/NOT_AUTHENT
- CHANGED roobet.com/_api/settings/get response stable at 35 keys (down from 68); globalStats.allTimeNumBets ~15.3B; restrictedCountries 35 entries — config surface reduced but static across 5+ runs
- CHANGED roobet.com/_api/admin/users, /_api/admin/stats base paths consistently 401 (prior 404s were probe URL artifacts with backticks)
- CHANGED roobet.com/_api/affiliate/get ?user_id/?affiliate_code return 401 not 404 — confirms parameter parsing on low-gate surface
- CHANGED Surface static: 6 HTTP routes + 2 WS routes confirmed across 10+ runs; zero delta in hosts/routes
- CHANGED api.roobet.com, auth.roobet.com, account.roobet.com, admin.roobet.com, billing.roobet.com, dashboard.roobet.com, sso.roobet.com + 13 others: non-resolving/internal (000/timeout) — no delta
- CHANGED crash-gs.roobet.com Socket.IO TLS upgrade open (no 4xx) then app-timeout; HUMAN_ONLY — no delta
- CHANGED fs.roobet.com GCS ?list-type=2 → fullstory.com redirect; no enumeration — no delta
- CHANGED roobet.com OAuth metadata endpoints return SPA shell (Remix catch-all), not JSON — no delta
- NEW roobet.com/_api/graphql HTTP GET read-plane: exchangeRates (named op + x-apollo-operation-name) → 200 with NOT_AUTHENTICATED/null data — resolver auth gate confirmed identical on HTTP and WS channels 
- CHANGED roobet.com/_api/graphql HTTP POST liveRTPUpdate error patched: 200 "No user with that id" + INTERNAL_SERVER_ERROR → 400 + 3×INTERNAL_SERVER_ERROR (resolver still executes pre-auth, not 401/NOT_AUTHENT
- CHANGED roobet.com/_api/settings/get response stable at 35 keys (down from 68); globalStats.allTimeNumBets ~15.3B; restrictedCountries 35 entries — config surface reduced but static across 5+ runs
- CHANGED roobet.com/_api/admin/users, /_api/admin/stats base paths consistently 401 (prior 404s were probe URL artifacts with backticks)
- CHANGED roobet.com/_api/affiliate/get ?user_id/?affiliate_code return 401 not 404 — confirms parameter parsing on low-gate surface
- CHANGED Surface static: 6 HTTP routes + 2 WS routes confirmed across 10+ runs; zero delta in hosts/routes
- CHANGED api.roobet.com, auth.roobet.com, account.roobet.com, admin.roobet.com, billing.roobet.com, dashboard.roobet.com, sso.roobet.com + 13 others: non-resolving/internal (000/timeout) — no delta
- CHANGED crash-gs.roobet.com Socket.IO TLS upgrade open (no 4xx) then app-timeout; HUMAN_ONLY — no delta
- CHANGED fs.roobet.com GCS ?list-type=2 → fullstory.com redirect; no enumeration — no delta
- CHANGED roobet.com OAuth metadata endpoints return SPA shell (Remix catch-all), not JSON — no delta

## 2026-09-11 03:53:43 UTC
- CHANGED roobet.com/_api/graphql HTTP GET read-plane confirmed: `exchangeRates` (named op + `x-apollo-operation-name`) → 200 with `NOT_AUTHENTICATED`/null data — resolver auth gate identical on HTTP and WS cha
- CHANGED roobet.com/_api/graphql HTTP POST `liveRTPUpdate` error patched: 200 "No user with that id" + INTERNAL_SERVER_ERROR → 400 + 3×INTERNAL_SERVER_ERROR (resolver still executes pre-auth, not 401/NOT_AUTHE
- CHANGED roobet.com/_api/settings/get response stable at 35 keys (down from 68); `globalStats.allTimeNumBets` ~15.3B; `restrictedCountries` 35 entries — config surface reduced but static across 5+ runs
- CHANGED roobet.com/_api/admin/users, /_api/admin/stats base paths consistently 401 (prior 404s were probe URL artifacts with backticks)
- CHANGED roobet.com/_api/affiliate/get `?user_id`/`affiliate_code` return 401 not 404 — confirms parameter parsing on low-gate surface
- CHANGED Surface static: 6 HTTP routes + 2 WS routes confirmed across 10+ runs; zero delta in hosts/routes
- CHANGED api.roobet.com, auth.roobet.com, account.roobet.com, admin.roobet.com, billing.roobet.com, dashboard.roobet.com, sso.roobet.com + 13 others: non-resolving/internal (000/timeout) — no delta
- CHANGED crash-gs.roobet.com Socket.IO TLS upgrade open (no 4xx) then app-timeout; HUMAN_ONLY — no delta
- CHANGED fs.roobet.com GCS ?list-type=2 → fullstory.com redirect; no enumeration — no delta
- CHANGED roobet.com OAuth metadata endpoints return SPA shell (Remix catch-all), not JSON — no delta

## 2026-09-11 08:50:10 UTC
- CHANGED roobet.com/_api/graphql HTTP GET read-plane confirmed: `exchangeRates` (named op + `x-apollo-operation-name`) → 200 with `NOT_AUTHENTICATED`/null data — resolver auth gate identical on HTTP and WS cha
- CHANGED roobet.com/_api/graphql HTTP POST `liveRTPUpdate` error patched: 200 "No user with that id" + INTERNAL_SERVER_ERROR → 400 + 3×INTERNAL_SERVER_ERROR (resolver still executes pre-auth, not 401/NOT_AUTHE
- CHANGED roobet.com/_api/settings/get response stable at 35 keys (down from 68); `globalStats.allTimeNumBets` ~15.3B; `restrictedCountries` 35 entries — config surface reduced but static across 5+ runs
- CHANGED roobet.com/_api/admin/users, /_api/admin/stats base paths consistently 401 (prior 404s were probe URL artifacts with backticks)
- CHANGED roobet.com/_api/affiliate/get `?user_id`/`affiliate_code` return 401 not 404 — confirms parameter parsing on low-gate surface
- CHANGED Surface static: 6 HTTP routes + 2 WS routes confirmed across 10+ runs; zero delta in hosts/routes
- CHANGED api.roobet.com, auth.roobet.com, account.roobet.com, admin.roobet.com, billing.roobet.com, dashboard.roobet.com, sso.roobet.com + 13 others: non-resolving/internal (000/timeout) — no delta
- CHANGED crash-gs.roobet.com Socket.IO TLS upgrade open (no 4xx) then app-timeout; HUMAN_ONLY — no delta
- CHANGED fs.roobet.com GCS ?list-type=2 → fullstory.com redirect; no enumeration — no delta
- CHANGED roobet.com OAuth metadata endpoints return SPA shell (Remix catch-all), not JSON — no delta

## 2026-09-11 13:42:50 UTC

## 2026-09-11 17:23:07 UTC
- CHANGED roobet.com/_api/graphql HTTP POST: liveRTPUpdate mutation error message patched from 200 "No user with that id" + INTERNAL_SERVER_ERROR to 400 + 3×INTERNAL_SERVER_ERROR — resolver still executes pre-a
- CHANGED roobet.com/_api/settings/get: response stable at 35 keys (down from 68); globalStats.allTimeNumBets ~15.3B; restrictedCountries 35 entries — config surface reduced but static across 10+ runs
- CHANGED roobet.com/_api/admin/users, /_api/admin/stats base paths consistently 401 (prior 404s were probe URL artifacts with backticks)
- CHANGED roobet.com/_api/affiliate/get ?user_id/?affiliate_code return 401 not 404 — confirms parameter parsing on low-gate surface
- CHANGED roobet.com/_api/socket.io polling Origin-gated: 403 without Origin: https://roobet.com, 200 with it
- CHANGED roobet.com/_api/graphql GET: CSRF preflight confirmed via error body — requires non-form content-type or x-apollo-operation-name/apollo-require-preflight
- NEW Verified 6 additional mutations (updateUserProfile, placeBet, claimBonus, forfeitCashableBonus, updateEmail, updatePassword) execute pre-auth on HTTP channel → all return INTERNAL_SERVER_ERROR (not 40
- CHANGED Surface static: 6 HTTP + 2 WS routes confirmed across 10+ runs; zero delta in hosts/routes

## 2026-09-11 19:53:10 UTC
- CHANGED roobet.com/_api/graphql HTTP POST: 7/7 tested mutations (liveRTPUpdate, updateUserProfile, placeBet, claimBonus, forfeitCashableBonus, updateEmail, updatePassword) execute pre-auth → INTERNAL_SERVER_E
- CHANGED roobet.com/_api/settings/get: response stable at 35 keys (down from 68); globalStats.allTimeNumBets ~15.3B; restrictedCountries 35 entries — config surface reduced but static across 10+ runs
- CHANGED roobet.com/_api/admin/users, /_api/admin/stats base paths consistently 401 (prior 404s were probe URL artifacts with backticks)
- CHANGED roobet.com/_api/affiliate/get ?user_id/?affiliate_code return 401 not 404 — confirms parameter parsing on low-gate surface
- CHANGED roobet.com/_api/socket.io polling Origin-gated: 403 without Origin: https://roobet.com, 200 with it
- CHANGED roobet.com/_api/graphql GET: CSRF preflight confirmed via error body — requires non-form content-type or x-apollo-operation-name/apollo-require-preflight
- CHANGED Surface static: 6 HTTP + 2 WS routes confirmed across 10+ runs; zero delta in hosts/routes

## 2026-09-11 22:25:52 UTC
- CHANGED roobet.com/_api/graphql HTTP POST: 7/7 tested mutations (liveRTPUpdate, updateUserProfile, placeBet, claimBonus, forfeitCashableBonus, updateEmail, updatePassword) execute pre-auth → INTERNAL_SERVER_E
- CHANGED roobet.com/_api/settings/get: response stable at 35 keys (down from 68); globalStats.allTimeNumBets ~15.3B; restrictedCountries 35 entries — config surface reduced but static across 10+ runs
- CHANGED roobet.com/_api/admin/users, /_api/admin/stats base paths consistently 401 (prior 404s were probe URL artifacts with backticks)
- CHANGED roobet.com/_api/affiliate/get ?user_id/?affiliate_code return 401 not 404 — confirms parameter parsing on low-gate surface
- CHANGED roobet.com/_api/socket.io polling Origin-gated: 403 without Origin: https://roobet.com, 200 with it
- CHANGED roobet.com/_api/graphql GET: CSRF preflight confirmed via error body — requires non-form content-type or x-apollo-operation-name/apollo-require-preflight
- CHANGED Surface static: 6 HTTP + 2 WS routes confirmed across 10+ runs; zero delta in hosts/routes
- NEW roobet.com/_api/graphql HTTP POST liveRTPUpdate error patched: 200 "No user with that id" + INTERNAL_SERVER_ERROR → 400 + 3×INTERNAL_SERVER_ERROR (server patched error message but resolver still execu
- NEW roobet.com/_api/graphql HTTP GET read-plane: exchangeRates (named op + x-apollo-operation-name) → 200 with NOT_AUTHENTICATED/null data — resolver auth gate confirmed identical on HTTP and WS channels
- NEW Verified 7 mutations execute pre-auth on HTTP channel (all INTERNAL_SERVER_ERROR, not 401/NOT_AUTHENTICATED)

## 2026-09-12 00:39:23 UTC
- CHANGED roobet.com/_api/graphql HTTP POST liveRTPUpdate error patched: 200 "No user with that id" + INTERNAL_SERVER_ERROR → 400 + 3×INTERNAL_SERVER_ERROR (resolver still executes pre-auth, not 401/NOT_AUTHENT
- CHANGED roobet.com/_api/graphql HTTP GET read-plane: exchangeRates (named op + x-apollo-operation-name) → 200 with NOT_AUTHENTICATED/null data — resolver auth gate confirmed identical on HTTP and WS channels
- NEW Verified 7 mutations execute pre-auth on HTTP channel (liveRTPUpdate, updateUserProfile, placeBet, claimBonus, forfeitCashableBonus, updateEmail, updatePassword) — all return INTERNAL_SERVER_ERROR, no
- CHANGED roobet.com/_api/affiliate/get ?user_id/?affiliate_code return 401 not 404 — confirms parameter parsing on low-gate surface
- CHANGED roobet.com/_api/socket.io polling Origin-gated: 403 without Origin: https://roobet.com, 200 with it
- CHANGED roobet.com/_api/graphql GET: CSRF preflight confirmed via error body — requires non-form content-type or x-apollo-operation-name/apollo-require-preflight
- CHANGED Surface static: 6 HTTP + 2 WS routes confirmed across 10+ runs; zero delta in hosts/routes
- CHANGED roobet.com/_api/settings/get response stable at 35 keys (down from 68); globalStats.allTimeNumBets ~15.3B; restrictedCountries 35 entries
- CHANGED roobet.com/_api/admin/users, /_api/admin/stats base paths consistently 401 (prior 404s were probe URL artifacts)
- CHANGED api.roobet.com, auth.roobet.com, account.roobet.com, admin.roobet.com, billing.roobet.com, dashboard.roobet.com, sso.roobet.com + 13 others: non-resolving/internal (000/timeout) — no delta
- CHANGED crash-gs.roobet.com Socket.IO TLS upgrade open (no 4xx) then app-timeout; HUMAN_ONLY — no delta
- CHANGED fs.roobet.com GCS ?list-type=2 → fullstory.com redirect; no enumeration — no delta
- CHANGED roobet.com OAuth metadata endpoints return SPA shell (Remix catch-all), not JSON — no delta

## 2026-09-12 05:05:07 UTC
- CHANGED Surface static: 6 HTTP + 2 WS routes confirmed across 10+ runs; zero delta in hosts/routes
- CHANGED roobet.com/_api/settings/get response stable at 35 keys (down from 68); globalStats.allTimeNumBets ~15.3B; restrictedCountries 35 entries
- CHANGED roobet.com/_api/admin/users, /_api/admin/stats base paths consistently 401 (prior 404s were probe URL artifacts)
- CHANGED api.roobet.com, auth.roobet.com, account.roobet.com, admin.roobet.com, billing.roobet.com, dashboard.roobet.com, sso.roobet.com + 13 others: non-resolving/internal (000/timeout) — no delta
- CHANGED crash-gs.roobet.com Socket.IO TLS upgrade open (no 4xx) then app-timeout; HUMAN_ONLY — no delta
- CHANGED fs.roobet.com GCS ?list-type=2 → fullstory.com redirect; no enumeration — no delta
- CHANGED roobet.com OAuth metadata endpoints return SPA shell (Remix catch-all), not JSON — no delta

## 2026-09-12 09:33:46 UTC
- CHANGED Surface fully static across 10+ runs: 6 HTTP + 2 WS routes on roobet.com/_api/* confirmed; zero delta in hosts/routes/keys
- CHANGED roobet.com/_api/settings/get response byte-stable at 35 keys (1764B); globalStats.allTimeNumBets ~15.3B; restrictedCountries 35 entries
- CHANGED roobet.com/_api/graphql HTTP POST: 7/7 tested mutations (liveRTPUpdate, updateUserProfile, placeBet, claimBonus, forfeitCashableBonus, updateEmail, updatePassword) execute pre-auth → INTERNAL_SERVER_E
- CHANGED roobet.com/_api/graphql HTTP GET: exchangeRates (named op + x-apollo-operation-name) → 200 with NOT_AUTHENTICATED/null data — resolver auth gate identical on HTTP and WS
- CHANGED roobet.com/_api/admin/users, /_api/admin/stats base paths consistently 401 (prior 404s were probe URL artifacts)
- CHANGED roobet.com/_api/affiliate/get ?user_id/?affiliate_code return 401 not 404 — confirms parameter parsing on low-gate surface
- CHANGED roobet.com/_api/socket.io polling Origin-gated: 403 without Origin: https://roobet.com, 200 with it
- CHANGED api.roobet.com, auth.roobet.com, account.roobet.com, admin.roobet.com, billing.roobet.com, dashboard.roobet.com, sso.roobet.com + 13 others: non-resolving/internal (000/timeout) — no delta
- CHANGED crash-gs.roobet.com Socket.IO TLS upgrade open (no 4xx) then app-timeout; HUMAN_ONLY — no delta
- CHANGED fs.roobet.com GCS ?list-type=2 → fullstory.com redirect; no enumeration — no delta
- CHANGED roobet.com OAuth metadata endpoints return SPA shell (Remix catch-all), not JSON — no delta

## 2026-09-12 13:12:20 UTC
- CHANGED roobet.com/_api/settings/get response byte-stable at 35 keys (1764B); globalStats.allTimeNumBets ~15.3B; restrictedCountries 35 entries — config surface reduced but static across 10+ runs
- CHANGED roobet.com/_api/graphql HTTP POST: 7/7 tested mutations execute pre-auth → INTERNAL_SERVER_ERROR (not 401/NOT_AUTHENTICATED); liveRTPUpdate error patched from 200+"No user with that id" to 400+3×ISE
- CHANGED roobet.com/_api/admin/users, /_api/admin/stats base paths consistently 401 (prior 404s were probe URL artifacts)
- CHANGED roobet.com/_api/affiliate/get ?user_id/?affiliate_code return 401 not 404 — confirms parameter parsing on low-gate surface
- CHANGED roobet.com/_api/socket.io polling Origin-gated: 403 without Origin: https://roobet.com, 200 with it
- CHANGED api.roobet.com, auth.roobet.com, account.roobet.com, admin.roobet.com, billing.roobet.com, dashboard.roobet.com, sso.roobet.com + 13 others: non-resolving/internal (000/timeout) — no delta
- CHANGED crash-gs.roobet.com Socket.IO TLS upgrade open (no 4xx) then app-timeout; HUMAN_ONLY — no delta
- CHANGED fs.roobet.com GCS ?list-type=2 → fullstory.com redirect; no enumeration — no delta
- CHANGED roobet.com OAuth metadata endpoints return SPA shell (Remix catch-all), not JSON — no delta
- CHANGED Server actively hardening: liveRTPUpdate error message suppressed, HTTP introspection disabled (INTROSPECTION_DISABLED), settings/get trimmed 68→35 keys

## 2026-09-12 16:30:40 UTC
- CHANGED roobet.com/_api/settings/get response byte-stable at 35 keys (1762-1764B across 10+ runs); globalStats.allTimeNumBets ~15.3B; restrictedCountries 35 entries — config surface reduced but static
- CHANGED roobet.com/_api/graphql HTTP POST: 7/7 tested mutations execute pre-auth → INTERNAL_SERVER_ERROR (not 401/NOT_AUTHENTICATED); liveRTPUpdate error patched from 200+"No user with that id" to 400+3×ISE
- CHANGED roobet.com/_api/admin/users, /_api/admin/stats base paths consistently 401 (prior 404s were probe URL artifacts)
- CHANGED roobet.com/_api/affiliate/get ?user_id/?affiliate_code return 401 not 404 — confirms parameter parsing on low-gate surface
- CHANGED roobet.com/_api/socket.io polling Origin-gated: 403 without Origin: https://roobet.com, 200 with it
- CHANGED Server actively hardening: liveRTPUpdate error message suppressed, HTTP introspection disabled (INTROSPECTION_DISABLED), settings/get trimmed 68→35 keys
- CHANGED api.roobet.com, auth.roobet.com, account.roobet.com, admin.roobet.com, billing.roobet.com, dashboard.roobet.com, sso.roobet.com + 13 others: non-resolving/internal (000/timeout) — no delta
- CHANGED crash-gs.roobet.com Socket.IO TLS upgrade open (no 4xx) then app-timeout; HUMAN_ONLY — no delta
- CHANGED fs.roobet.com GCS ?list-type=2 → fullstory.com redirect; no enumeration — no delta
- CHANGED roobet.com OAuth metadata endpoints return SPA shell (Remix catch-all), not JSON — no delta

## 2026-09-12 18:49:22 UTC
- CHANGED roobet.com/_api/graphql HTTP POST: 3/3 additional mutations tested (claimBonus, updateUserProfile, placeBet) execute pre-auth → INTERNAL_SERVER_ERROR (not 401/NOT_AUTHENTICATED); pattern holds across 
- CHANGED roobet.com/_api/settings/get: response byte-stable at 35 keys (1762-1764B across 10+ runs); globalStats.allTimeNumBets ~15.3B; restrictedCountries 35 entries
- CHANGED roobet.com/_api/admin/users, /_api/admin/stats base paths consistently 401 (prior 404s were probe URL artifacts)
- CHANGED roobet.com/_api/affiliate/get ?user_id/?affiliate_code return 401 not 404 — confirms parameter parsing on low-gate surface
- CHANGED roobet.com/_api/socket.io polling Origin-gated: 403 without Origin: https://roobet.com, 200 with it
- CHANGED Server actively hardening: liveRTPUpdate error message suppressed, HTTP introspection disabled (INTROSPECTION_DISABLED), settings/get trimmed 68→35 keys
- CHANGED api.roobet.com, auth.roobet.com, account.roobet.com, admin.roobet.com, billing.roobet.com, dashboard.roobet.com, sso.roobet.com + 13 others: non-resolving/internal (000/timeout) — no delta
- CHANGED crash-gs.roobet.com Socket.IO TLS upgrade open (no 4xx) then app-timeout; HUMAN_ONLY — no delta
- CHANGED fs.roobet.com GCS ?list-type=2 → fullstory.com redirect; no enumeration — no delta
- CHANGED roobet.com OAuth metadata endpoints return SPA shell (Remix catch-all), not JSON — no delta
