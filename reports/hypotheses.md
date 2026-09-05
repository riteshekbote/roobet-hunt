# Hypotheses (ranked)

## RANKED HYPOTHESES 2026-09-02 21:54:54 UTC

## RANKED HYPOTHESES 2026-09-02 23:55:46 UTC

## RANKED HYPOTHESES 2026-09-03 03:47:00 UTC

## RANKED HYPOTHESES 2026-09-03 08:51:33 UTC

## RANKED HYPOTHESES 2026-09-03 13:28:47 UTC

## RANKED HYPOTHESES 2026-09-03 17:18:26 UTC
- [65] api.roobet.com: API Mass Assignment on User Wallet/Profile Update (from art/lead_nemotron3.txt)
- [55] api.roobet.com:8088: Exposed/internal GraphQL backend behind api.roobet.com with admin WS port 8088 (from art/lead_bigpickle.txt)
- NEXT(hypotheses-bigpickle.txt): PROBE: GET https://fs.roobet.com/?list-type=2&max-keys=1 then GET https://fs.roobet.com/s/ (compare 200 ListBucketResult vs 403); also GET https://fs.roobet.com
- NEXT(hypotheses-nemotron3.txt): SCAN: Passive HTTP probe all 20 hosts (HEAD /, 1 rps) to confirm live endpoints, server headers, and discover API/auth paths (/.well-known/oauth-authorization-s
- LEARN: REJECTED OTHER @ roobet.com bundle: delivered ContentStack tokens are public-by-design; not reportable. No delta in server surface from prior runs.
- LEARN: REJECTED OTHER @ api.roobet.com: mass assignment hypothesis parked — no live endpoint confirmed, auth state unknown.
- LEARN: REJECTED OATH @ auth.roobet.com: OAuth redirect_uri bypass parked — endpoint path unknown, passive probe needed first.
- LEARN: REJECTED IDOR @ account.roobet.com: IDOR hypothesis parked — requires auth + user ID format discovery.

## RANKED HYPOTHESES 2026-09-03 20:05:21 UTC
- [55] api.roobet.com: GraphQL Introspection via Aliased Query on api.roobet.com (from art/lead_nemotron3.txt)
- [45] fs.roobet.com: fs.roobet.com GCS bucket object listing exposure (from art/lead_bigpickle.txt)
- NEXT(hypotheses-nemotron3.txt): PROBE: GET https://roobet.com/.well-known/oauth-authorization-server && GET https://roobet.com/.well-known/openid-configuration
- NEXT(hypotheses-bigpickle.txt): PROBE: GET https://fs.roobet.com/?list-type=2&max-keys=1 then GET https://fs.roobet.com/s/ (compare 200 ListBucketResult XML vs 403 AccessDenied); also GET http
- LEARN: REJECTED OTHER @ api.roobet.com: mass assignment hypothesis parked — 403 block confirms Cloudflare bot management; no live API endpoint reachable without valid 
- LEARN: REJECTED OATH @ auth.roobet.com: OAuth redirect_uri bypass parked — auth.roobet.com does not resolve/respond; endpoint path unknown.
- LEARN: REJECTED IDOR @ account.roobet.com: IDOR hypothesis parked — account.roobet.com does not resolve/respond; no user ID format discoverable.
- LEARN: ACCEPTED MISCONFIG @ fs.roobet.com: GCS bucket allows ListBucketResult via ?list-type=2 but serves only FullStory assets; low impact.
- LEARN: REJECTED OTHER @ roobet.com bundle: ContentStack delivery tokens public-by-design; preview token low-severity, program-excluded.
- LEARN: PARKED api.roobet.com mass-assignment: no live endpoint confirmed, auth unknown.
- LEARN: PARKED auth.roobet.com OAuth redirect_uri: endpoint path unknown, passive probe needed.
- LEARN: PARKED account.roobet.com IDOR: requires auth + user ID format discovery.

## RANKED HYPOTHESES 2026-09-03 22:40:48 UTC
- [65] roobet.com: Remix SPA Catch-All Route Masks API Endpoints on roobet.com (from art/lead_nemotron3.txt)
- [55] api.roobet.com:8088: Exposed/internal GraphQL backend behind api.roobet.com with admin WS port 8088 (from art/lead_bigpickle.txt)
- NEXT(hypotheses-bigpickle.txt): PROBE: GET https://fs.roobet.com/?list-type=2&max-keys=1 then GET https://fs.roobet.com/s/ (compare 200 ListBucketResult vs 403); also GET https://fs.roobet.com
- NEXT(hypotheses-nemotron3.txt): PROBE: POST https://api.roobet.com/graphql -H "Content-Type: application/json" -H "Origin: https://roobet.com" -H "Referer: https://roobet.com/" -d '{"query":"{
- LEARN: REJECTED OTHER @ roobet.com bundle: delivered ContentStack tokens are public-by-design; not reportable. No delta in server surface from prior runs.
- LEARN: REJECTED OTHER @ roobet.com bundle: ContentStack delivery tokens public-by-design; preview token low-severity, program-excluded.
- LEARN: PARKED api.roobet.com mass-assignment: no live endpoint confirmed, auth unknown.
- LEARN: PARKED auth.roobet.com OAuth redirect_uri: endpoint path unknown, passive probe needed.
- LEARN: PARKED account.roobet.com IDOR: requires auth + user ID format discovery.
- LEARN: REJECTED OTHER @ roobet.com bundle: ContentStack delivery tokens public-by-design; preview token low-severity, program-excluded.
- LEARN: PARKED api.roobet.com mass-assignment: no live endpoint confirmed, auth unknown.
- LEARN: PARKED auth.roobet.com OAuth redirect_uri: endpoint path unknown, passive probe needed.
- LEARN: PARKED account.roobet.com IDOR: requires auth + user ID format discovery.
- LEARN: REJECTED OTHER @ api.roobet.com: mass assignment hypothesis parked — no live endpoint confirmed, auth state unknown.
- LEARN: REJECTED OATH @ auth.roobet.com: OAuth redirect_uri bypass parked — endpoint path unknown, passive probe needed first.
- LEARN: REJECTED IDOR @ account.roobet.com: IDOR hypothesis parked — requires auth + user ID format discovery.
- LEARN: REJECTED OTHER @ api.roobet.com: mass assignment hypothesis parked — 403 block confirms Cloudflare bot management; no live API endpoint reachable without valid 
- LEARN: REJECTED OATH @ auth.roobet.com: OAuth redirect_uri bypass parked — auth.roobet.com does not resolve/respond; endpoint path unknown.
- LEARN: REJECTED IDOR @ account.roobet.com: IDOR hypothesis parked — account.roobet.com does not resolve/respond; no user ID format discoverable.
- LEARN: ACCEPTED MISCONFIG @ fs.roobet.com: GCS bucket allows ListBucketResult via ?list-type=2 but serves only FullStory assets; low impact.
- LEARN: REJECTED MISCONFIG @ roobet-dev-public-images-prod S3: bucket 403-locked on list+location; no public-object exposure.
- LEARN: REJECTED OATH @ roobet.com: .well-known oauth-authorization-server + openid-configuration return SPA catch-all HTML, not real OAuth metadata; no issuer/endpoint
- LEARN: ACCEPTED OTHER @ roobet.com _api/: two undocumented live server routes confirmed reachable past Cloudflare bot-gate (settings/get, tp-games/essentials); new low
- LEARN: REJECTED MISCONFIG @ roobet-dev-public-images-prod S3: bucket 403-locked on list+location; no public-object exposure.
- LEARN: REJECTED OATH @ roobet.com: `/.well-known/oauth-authorization-server` + openid-configuration return SPA catch-all HTML, not real OAuth metadata; no issuer/endpo
- LEARN: ACCEPTED OTHER @ roobet.com `_api/`: two undocumented live server routes confirmed reachable past Cloudflare bot-gate (settings/get, tp-games/essentials); new l
- LEARN: REJECTED MISCONFIG @ roobet.com: OAuth metadata endpoints return SPA shell (catch-all route), not JSON configuration.
- LEARN: REJECTED MISCONFIG @ fs.roobet.com: GCS bucket ?list-type=2 redirects to fullstory.com; no object enumeration possible.
- LEARN: REJECTED OTHER @ api.roobet.com: GraphQL endpoint blocked by Cloudflare bot management (403) without valid Origin/Referer.
- LEARN: ACCEPTED MISCONFIG @ roobet.com: Remix catch-all route masks potential API endpoints under /api/* paths.
- LEARN: PARKED api.roobet.com Cloudflare bypass: requires valid browser headers/session to test.
- LEARN: PARKED auth.roobet.com/account.roobet.com/admin.roobet.com: subdomains unresponsive; no attack surface confirmed.

## RANKED HYPOTHESES 2026-09-04 00:31:27 UTC
- [55] roobet.com/_api/*: Undocumented _api/* Server Routes Expose Hidden Business Logic Surface (from art/lead_nemotron3.txt)
- [55] api.roobet.com:8088: Exposed/internal GraphQL backend behind api.roobet.com with admin WS port 8088 (from art/lead_bigpickle.txt)
- NEXT(hypotheses-nemotron3.txt): PROBE: GET https://roobet.com/_api/{auth,user,wallet,config,benefits,trivia,promotion,affiliate,notifications,jackpot,leaderboard}/get + variants (1 rps), recor
- NEXT(hypotheses-bigpickle.txt): PROBE: GET https://fs.roobet.com/?list-type=2&max-keys=1 then GET https://fs.roobet.com/s/ (compare 200 ListBucketResult vs 403); also GET https://fs.roobet.com
- LEARN: REJECTED MISCONFIG @ roobet.com: OAuth metadata endpoints return SPA shell (catch-all route), not JSON configuration
- LEARN: REJECTED MISCONFIG @ fs.roobet.com: GCS bucket ?list-type=2 redirects to fullstory.com; no object enumeration possible
- LEARN: REJECTED OTHER @ api.roobet.com: GraphQL endpoint blocked by Cloudflare bot management (403) without valid Origin/Referer/browser session
- LEARN: ACCEPTED MISCONFIG @ roobet.com: Remix catch-all route masks potential API endpoints under /api/* paths
- LEARN: ACCEPTED OTHER @ roobet.com _api/: two undocumented live server routes confirmed reachable past Cloudflare bot-gate (settings/get, tp-games/essentials); new low
- LEARN: PARKED api.roobet.com Cloudflare bypass: requires valid browser headers/session/turnstile to test
- LEARN: PARKED auth.roobet.com/account.roobet.com/admin.roobet.com: subdomains unresponsive; no attack surface confirmed
- LEARN: PARKED crash-gs.roobet.com unauthenticated socket: requires browser/WS tooling, HUMAN_ONLY
- LEARN: REJECTED OTHER @ roobet.com bundle: delivered ContentStack tokens are public-by-design; not reportable. No delta in server surface from prior runs.
- LEARN: REJECTED OTHER @ roobet.com bundle: ContentStack delivery tokens public-by-design; preview token low-severity, program-excluded.
- LEARN: PARKED api.roobet.com mass-assignment: no live endpoint confirmed, auth unknown.
- LEARN: PARKED auth.roobet.com OAuth redirect_uri: endpoint path unknown, passive probe needed.
- LEARN: PARKED account.roobet.com IDOR: requires auth + user ID format discovery.
- LEARN: REJECTED OTHER @ roobet.com bundle: ContentStack delivery tokens public-by-design; preview token low-severity, program-excluded.
- LEARN: PARKED api.roobet.com mass-assignment: no live endpoint confirmed, auth unknown.
- LEARN: PARKED auth.roobet.com OAuth redirect_uri: endpoint path unknown, passive probe needed.
- LEARN: PARKED account.roobet.com IDOR: requires auth + user ID format discovery.
- LEARN: REJECTED OTHER @ api.roobet.com: mass assignment hypothesis parked — no live endpoint confirmed, auth state unknown.
- LEARN: REJECTED OATH @ auth.roobet.com: OAuth redirect_uri bypass parked — endpoint path unknown, passive probe needed first.
- LEARN: REJECTED IDOR @ account.roobet.com: IDOR hypothesis parked — requires auth + user ID format discovery.
- LEARN: REJECTED OTHER @ api.roobet.com: mass assignment hypothesis parked — 403 block confirms Cloudflare bot management; no live API endpoint reachable without valid 
- LEARN: REJECTED OATH @ auth.roobet.com: OAuth redirect_uri bypass parked — auth.roobet.com does not resolve/respond; endpoint path unknown.
- LEARN: REJECTED IDOR @ account.roobet.com: IDOR hypothesis parked — account.roobet.com does not resolve/respond; no user ID format discoverable.
- LEARN: ACCEPTED MISCONFIG @ fs.roobet.com: GCS bucket allows ListBucketResult via ?list-type=2 but serves only FullStory assets; low impact.
- LEARN: REJECTED MISCONFIG @ roobet-dev-public-images-prod S3: bucket 403-locked on list+location; no public-object exposure.
- LEARN: REJECTED OATH @ roobet.com: .well-known oauth-authorization-server + openid-configuration return SPA catch-all HTML, not real OAuth metadata; no issuer/endpoint
- LEARN: ACCEPTED OTHER @ roobet.com _api/: two undocumented live server routes confirmed reachable past Cloudflare bot-gate (settings/get, tp-games/essentials); new low
- LEARN: REJECTED MISCONFIG @ roobet-dev-public-images-prod S3: bucket 403-locked on list+location; no public-object exposure.
- LEARN: REJECTED OATH @ roobet.com: `/.well-known/oauth-authorization-server` + openid-configuration return SPA catch-all HTML, not real OAuth metadata; no issuer/endpo
- LEARN: ACCEPTED OTHER @ roobet.com `_api/`: two undocumented live server routes confirmed reachable past Cloudflare bot-gate (settings/get, tp-games/essentials); new l
- LEARN: ACCEPTED OTHER @ roobet.com _api/: two undocumented live server routes confirmed reachable past Cloudflare bot-gate (settings/get, tp-games/essentials); new low
- LEARN: ACCEPTED OTHER @ roobet.com `_api/`: two undocumented live server routes confirmed reachable past Cloudflare bot-gate (settings/get, tp-games/essentials); new l

## RANKED HYPOTHESES 2026-09-04 05:08:52 UTC
- [65] roobet.com/_api/*: Undocumented _api/* Server Routes Expose Hidden Business Logic Surface (from art/lead_nemotron3.txt)
- NEXT(hypotheses-nemotron3.txt): PROBE: GET https://roobet.com/_api/{auth,user,wallet,config,benefits,trivia,promotion,affiliate,notifications,jackpot,leaderboard}/get + variants (1 rps), recor
- LEARN: REJECTED MISCONFIG @ roobet.com: OAuth metadata endpoints return SPA shell (catch-all route), not JSON configuration
- LEARN: REJECTED MISCONFIG @ fs.roobet.com: GCS bucket ?list-type=2 redirects to fullstory.com; no object enumeration possible
- LEARN: REJECTED OTHER @ api.roobet.com: GraphQL endpoint blocked by Cloudflare bot management (403) without valid Origin/Referer/browser session
- LEARN: ACCEPTED MISCONFIG @ roobet.com: Remix catch-all route masks potential API endpoints under /api/* paths
- LEARN: ACCEPTED OTHER @ roobet.com _api/: two undocumented live server routes confirmed reachable past Cloudflare bot-gate (settings/get, tp-games/essentials); new low
- LEARN: PARKED api.roobet.com Cloudflare bypass: requires valid browser headers/session/turnstile to test
- LEARN: PARKED auth.roobet.com/account.roobet.com/admin.roobet.com: subdomains unresponsive; no attack surface confirmed
- LEARN: PARKED crash-gs.roobet.com unauthenticated socket: requires browser/WS tooling, HUMAN_ONLY

## RANKED HYPOTHESES 2026-09-04 09:52:31 UTC
- [65] roobet.com/_api/*: Undocumented _api/* Server Routes Expose Hidden Business Logic Surface (from art/lead_nemotron3.txt)
- [62] roobet.com/_api/admin/*: Admin API surface accessible on low-gate roobet.com/_api/* bypasses Cloudflare bot-management (from art/lead_bigpickle.txt)
- NEXT(hypotheses-nemotron3.txt): PROBE: GET https://roobet.com/_api/{auth,user,wallet,config,benefits,trivia,promotion,affiliate,notifications,jackpot,leaderboard}/get + variants (1 rps), recor
- NEXT(hypotheses-bigpickle.txt): HUMAN: Test `_api/admin/users` and `_api/admin/stats` with a valid Roobet user session cookie to determine if normal-user auth grants admin access (privilege es
- LEARN: REJECTED MISCONFIG @ roobet.com: OAuth metadata endpoints return SPA shell (catch-all route), not JSON configuration
- LEARN: REJECTED MISCONFIG @ fs.roobet.com: GCS bucket ?list-type=2 redirects to fullstory.com; no object enumeration possible
- LEARN: REJECTED OTHER @ api.roobet.com: GraphQL endpoint blocked by Cloudflare bot management (403) without valid Origin/Referer/browser session
- LEARN: ACCEPTED MISCONFIG @ roobet.com: Remix catch-all route masks potential API endpoints under /api/* paths
- LEARN: ACCEPTED OTHER @ roobet.com _api/: two undocumented live server routes confirmed reachable past Cloudflare bot-gate (settings/get, tp-games/essentials); new low
- LEARN: PARKED api.roobet.com Cloudflare bypass: requires valid browser headers/session/turnstile to test
- LEARN: PARKED auth.roobet.com/account.roobet.com/admin.roobet.com: subdomains unresponsive; no attack surface confirmed
- LEARN: PARKED crash-gs.roobet.com unauthenticated socket: requires browser/WS tooling, HUMAN_ONLY
- LEARN: ACCEPTED MISCONFIG @ roobet.com/_api/admin/*: admin routes (admin/users, admin/stats) exist on low-gate surface; return 401 Unauthorized; not behind Cloudflare 
- LEARN: ACCEPTED OTHER @ roobet.com/_api/affiliate/get: affiliate endpoint exists on low-gate surface; 401 auth-gated; potential IDOR target.
- LEARN: ACCEPTED OTHER @ roobet.com/_api/settings/get: full internal config dump (IP, sessionId, restricted countries, withdraw flags, geo inference) — operational inte
- LEARN: ACCEPTED OTHER @ roobet.com/_api/tp-games/essentials: 9MB game catalog dump; internal S3 bucket reference; low severity.

## RANKED HYPOTHESES 2026-09-04 14:20:04 UTC
- [70] roobet.com/_api/admin/*: Admin API Surface Accessible via Low-Gate _api/* Routes (from art/lead_nemotron3.txt)
- [55] roobet.com/_api/admin/users: Admin API privilege escalation via normal user session (from art/lead_bigpickle.txt)
- NEXT(hypotheses-bigpickle.txt): HUMAN: Test `_api/admin/users` with a valid Roobet user session cookie (`connect.sid`) to determine if normal-user auth grants admin access. Requires: (1) sign 
- NEXT(hypotheses-nemotron3.txt): PROBE: GET https://roobet.com/_api/admin/users && GET https://roobet.com/_api/admin/stats && GET https://roobet.com/_api/affiliate/get (1 rps each) with valid R
- LEARN: ACCEPTED OTHER @ roobet.com/_api/*: Full enumeration complete — 40 route candidates tested, exactly 6 live routes confirmed (settings/get 200, tp-games/essentia
- LEARN: ACCEPTED OTHER @ roobet.com auth/logout: Auth mechanism revealed — Express.js session cookies (`connect.sid` HttpOnly + `userId` non-HttpOnly + `twofactorRequir
- LEARN: REJECTED OTHER @ roobet.com/_api/*: 34 of 40 candidates returned 404 SPA shell. Route family is not large — only 6 registered routes exist.
- LEARN: ACCEPTED MISCONFIG @ roobet.com/_api/admin/*: admin routes (admin/users, admin/stats) exist on low-gate surface; return 401 Unauthorized; not behind Cloudflare 
- LEARN: ACCEPTED OTHER @ roobet.com/_api/affiliate/get: affiliate endpoint exists on low-gate surface; 401 auth-gated; potential IDOR target
- LEARN: ACCEPTED OTHER @ roobet.com/_api/settings/get: full internal config dump (IP, sessionId, restricted countries, withdraw flags, geo inference) — operational inte
- LEARN: ACCEPTED OTHER @ roobet.com/_api/tp-games/essentials: 9MB game catalog dump; internal S3 bucket reference; low severity
- LEARN: REJECTED MISCONFIG @ roobet.com: OAuth metadata endpoints return SPA shell (catch-all route), not JSON configuration
- LEARN: REJECTED MISCONFIG @ fs.roobet.com: GCS bucket ?list-type=2 redirects to fullstory.com; no object enumeration possible
- LEARN: REJECTED OTHER @ api.roobet.com: GraphQL endpoint blocked by Cloudflare bot management (403) without valid Origin/Referer/browser session
- LEARN: ACCEPTED MISCONFIG @ roobet.com: Remix catch-all route masks potential API endpoints under /api/* paths
- LEARN: ACCEPTED OTHER @ roobet.com _api/: two undocumented live server routes confirmed reachable past Cloudflare bot-gate (settings/get, tp-games/essentials); new low
- LEARN: PARKED api.roobet.com Cloudflare bypass: requires valid browser headers/session/turnstile to test
- LEARN: PARKED auth.roobet.com/account.roobet.com/admin.roobet.com: subdomains unresponsive; no attack surface confirmed
- LEARN: PARKED crash-gs.roobet.com unauthenticated socket: requires browser/WS tooling, HUMAN_ONLY

## RANKED HYPOTHESES 2026-09-04 17:53:31 UTC
- [75] roobet.com/_api/admin/*: Admin API Privilege Escalation via Low-Gate _api/* Routes (from art/lead_nemotron3.txt)
- NEXT(hypotheses-nemotron3.txt): PROBE: GET https://roobet.com/_api/admin/users && GET https://roobet.com/_api/admin/stats && GET https://roobet.com/_api/affiliate/get (1 rps each) with valid R
- LEARN: ACCEPTED MISCONFIG @ roobet.com/_api/admin/*: admin routes (admin/users, admin/stats) exist on low-gate surface; return 401 Unauthorized; not behind Cloudflare 
- LEARN: ACCEPTED OTHER @ roobet.com/_api/affiliate/get: affiliate endpoint exists on low-gate surface; 401 auth-gated; potential IDOR target
- LEARN: ACCEPTED OTHER @ roobet.com/_api/settings/get: full internal config dump (IP, sessionId, restricted countries, withdraw flags, geo inference) — operational inte
- LEARN: ACCEPTED OTHER @ roobet.com/_api/tp-games/essentials: 9MB game catalog dump; internal S3 bucket reference; low severity
- LEARN: ACCEPTED OTHER @ roobet.com/_api/*: Full enumeration complete — 40 route candidates tested, exactly 6 live routes confirmed (settings/get 200, tp-games/essentia
- LEARN: ACCEPTED OTHER @ roobet.com auth/logout: Auth mechanism revealed — Express.js session cookies (connect.sid HttpOnly + userId non-HttpOnly + twofactorRequired). 
- LEARN: REJECTED MISCONFIG @ roobet.com: OAuth metadata endpoints return SPA shell (catch-all route), not JSON configuration
- LEARN: REJECTED MISCONFIG @ fs.roobet.com: GCS bucket ?list-type=2 redirects to fullstory.com; no object enumeration possible
- LEARN: REJECTED OTHER @ api.roobet.com: GraphQL endpoint blocked by Cloudflare bot management (403) without valid Origin/Referer/browser session
- LEARN: ACCEPTED MISCONFIG @ roobet.com: Remix catch-all route masks potential API endpoints under /api/* paths
- LEARN: PARKED api.roobet.com Cloudflare bypass: requires valid browser headers/session/turnstile to test
- LEARN: PARKED auth.roobet.com/account.roobet.com/admin.roobet.com: subdomains unresponsive; no attack surface confirmed
- LEARN: PARKED crash-gs.roobet.com unauthenticated socket: requires browser/WS tooling, HUMAN_ONLY

## RANKED HYPOTHESES 2026-09-04 20:00:09 UTC
- [75] roobet.com/_api/admin/*: Admin API Privilege Escalation via Low-Gate _api/* Routes (from art/lead_nemotron3.txt)
- [55] roobet.com/_api/admin/users: Admin API privilege escalation via normal user session (from art/lead_bigpickle.txt)
- NEXT(hypotheses-bigpickle.txt): HUMAN: Test `_api/admin/users` and `_api/admin/stats` with a valid Roobet user session (`connect.sid`) to confirm vertical privilege escalation (200 = user list
- NEXT(hypotheses-nemotron3.txt): PROBE: GET https://roobet.com/_api/admin/users && GET https://roobet.com/_api/admin/stats && GET https://roobet.com/_api/affiliate/get (1 rps each) with valid R
- LEARN: REJECTED OTHER @ roobet.com/_api/settings/get: XFF/query/Cookie/Referer input is NOT reflected (ip=server-observed egress, sessionId rotates per-request, auth c
- LEARN: REJECTED MISCONFIG @ api.roobet.com: raw WS upgrade to /graphql on 443+8443 => HTTP 403 from Cloudflare edge — bot-gate enforces WS, admin port 8088 unreachable
- LEARN: ACCEPTED OTHER @ crash-gs.roobet.com: TLS upgrade to socket.io endpoint stays open (no 4xx) then app-layer timeout = live Socket.IO server, passive curl insuffi
- LEARN: ACCEPTED OTHER @ roobet.com /pusher/auth + /pusher/user-auth: POST=>405 (live route), GET=>200 SPA catch-all; POST-only auth endpoints requiring valid session +
- LEARN: ACCEPTED OTHER @ api.roobet.com bundle: re-analysis found NO new Roobet-owned hosts/routes; FastTrack config is 3P (out of scope).
- LEARN: REJECTED OTHER @ roobet.com/_api/settings/get: XFF/query/Cookie/Referer input NOT reflected (`ip`=server-observed egress, sessionId rotates per-request, auth co
- LEARN: REJECTED MISCONFIG @ api.roobet.com: raw WS upgrade /graphql on 443+8443 ⇒ HTTP 403 (Cloudflare edge) — bot-gate enforces WS; admin port 8088 unreachable; needs
- LEARN: ACCEPTED OTHER @ crash-gs.roobet.com: socket.io TLS upgrade stays open (no 4xx) then app-layer timeout — live Socket.IO server, HUMAN_ONLY.
- LEARN: ACCEPTED OTHER @ roobet.com /pusher/auth + /pusher/user-auth: POST⇒405 (live), GET⇒200 SPA shell; POST-only auth endpoints, need session.
- LEARN: ACCEPTED OTHER @ api.roobet.com bundle: no new Roobet-owned subdomains/routes; FastTrack config URL is 3P (out of scope).
- LEARN: ACCEPTED MISCONFIG @ roobet.com/_api/admin/*: admin routes (admin/users, admin/stats) exist on low-gate surface; return 401 Unauthorized; not behind Cloudflare 
- LEARN: ACCEPTED OTHER @ roobet.com/_api/affiliate/get: affiliate endpoint exists on low-gate surface; 401 auth-gated; potential IDOR target
- LEARN: ACCEPTED OTHER @ roobet.com/_api/settings/get: full internal config dump (IP, sessionId, restricted countries, withdraw flags, geo inference) — operational inte
- LEARN: ACCEPTED OTHER @ roobet.com/_api/tp-games/essentials: 9MB game catalog dump; internal S3 bucket reference; low severity
- LEARN: ACCEPTED OTHER @ roobet.com/_api/*: Full enumeration complete — 40 route candidates tested, exactly 6 live routes confirmed (settings/get 200, tp-games/essentia
- LEARN: ACCEPTED OTHER @ roobet.com auth/logout: Auth mechanism revealed — Express.js session cookies (connect.sid HttpOnly + userId non-HttpOnly + twofactorRequired). 
- LEARN: REJECTED MISCONFIG @ roobet.com: OAuth metadata endpoints return SPA shell (catch-all route), not JSON configuration
- LEARN: REJECTED MISCONFIG @ fs.roobet.com: GCS bucket ?list-type=2 redirects to fullstory.com; no object enumeration possible
- LEARN: REJECTED OTHER @ api.roobet.com: GraphQL endpoint blocked by Cloudflare bot management (403) without valid Origin/Referer/browser session
- LEARN: ACCEPTED MISCONFIG @ roobet.com: Remix catch-all route masks potential API endpoints under /api/* paths
- LEARN: PARKED api.roobet.com Cloudflare bypass: requires valid browser headers/session/turnstile to test
- LEARN: PARKED auth.roobet.com/account.roobet.com/admin.roobet.com: subdomains unresponsive; no attack surface confirmed
- LEARN: PARKED crash-gs.roobet.com unauthenticated socket: requires browser/WS tooling, HUMAN_ONLY

## RANKED HYPOTHESES 2026-09-04 22:18:36 UTC
- [65] roobet.com/_api/affiliate/get: Affiliate Endpoint IDOR/BOLA on Low-Gate Surface (from art/lead_nemotron3.txt)
- NEXT(hypotheses-nemotron3.txt): PROBE: GET https://roobet.com/_api/admin/users && GET https://roobet.com/_api/admin/stats && GET https://roobet.com/_api/affiliate/get (1 rps each) with valid R
- LEARN: ACCEPTED MISCONFIG @ roobet.com/_api/admin/*: admin routes (admin/users, admin/stats) exist on low-gate surface; return 401 Unauthorized; not behind Cloudflare 
- LEARN: ACCEPTED OTHER @ roobet.com/_api/affiliate/get: affiliate endpoint exists on low-gate surface; 401 auth-gated; potential IDOR target
- LEARN: ACCEPTED OTHER @ roobet.com/_api/settings/get: full internal config dump (IP, sessionId, restricted countries, withdraw flags, geo inference) — operational inte
- LEARN: ACCEPTED OTHER @ roobet.com/_api/tp-games/essentials: 9MB game catalog dump; internal S3 bucket reference; low severity
- LEARN: ACCEPTED OTHER @ roobet.com/_api/*: Full enumeration complete — 40 route candidates tested, exactly 6 live routes confirmed (settings/get 200, tp-games/essentia
- LEARN: ACCEPTED OTHER @ roobet.com auth/logout: Auth mechanism revealed — Express.js session cookies (connect.sid HttpOnly + userId non-HttpOnly + twofactorRequired). 
- LEARN: REJECTED MISCONFIG @ roobet.com: OAuth metadata endpoints return SPA shell (catch-all route), not JSON configuration
- LEARN: REJECTED MISCONFIG @ fs.roobet.com: GCS bucket ?list-type=2 redirects to fullstory.com; no object enumeration possible
- LEARN: REJECTED OTHER @ api.roobet.com: GraphQL endpoint blocked by Cloudflare bot management (403) without valid Origin/Referer/browser session
- LEARN: ACCEPTED MISCONFIG @ roobet.com: Remix catch-all route masks potential API endpoints under /api/* paths
- LEARN: PARKED api.roobet.com Cloudflare bypass: requires valid browser headers/session/turnstile to test
- LEARN: PARKED auth.roobet.com/account.roobet.com/admin.roobet.com: subdomains unresponsive; no attack surface confirmed
- LEARN: PARKED crash-gs.roobet.com unauthenticated socket: requires browser/WS tooling, HUMAN_ONLY

## RANKED HYPOTHESES 2026-09-05 00:15:44 UTC
- [75] roobet.com/_api/admin/users: Admin API Privilege Escalation via Low-Gate _api/* Routes (from art/lead_nemotron3.txt)
- [55] roobet.com/_api/admin/users: Admin API privilege escalation via normal user session (from art/lead_bigpickle.txt)
- NEXT(hypotheses-bigpickle.txt): HUMAN: With a valid Roobet session, read-only GET `https://roobet.com/_api/admin/users` then `/stats` at 1 rps; 200-with-user-list ⇒ CRITICAL vertical priv-esc 
- NEXT(hypotheses-nemotron3.txt): PROBE: GET https://roobet.com/_api/admin/users && GET https://roobet.com/_api/admin/stats && GET https://roobet.com/_api/affiliate/get (1 rps each) with valid R
- LEARN: REJECTED OTHER @ roobet.com/_api/settings/get: XFF/query/Referer/Cookie input NOT reflected (`ip`=server-observed egress, sessionId rotates per-request) — no re
- LEARN: REJECTED MISCONFIG @ api.roobet.com: raw WS upgrade /graphql on 443+8443 ⇒ HTTP 403 (Cloudflare edge); admin port 8088 unreachable — needs Turnstile-passing bro
- LEARN: ACCEPTED OTHER @ crash-gs.roobet.com: socket.io TLS upgrade stays open (no 4xx) then app-layer timeout — live Socket.IO game-server, HUMAN_ONLY.
- LEARN: ACCEPTED OTHER @ roobet.com /pusher/auth + /pusher/user-auth: POST⇒405 (live), GET⇒200 SPA shell; session + exact body required.
- LEARN: ACCEPTED OTHER @ api.roobet.com bundle: no new Roobet-owned subdomains/routes; FastTrack config is 3P (out of scope).
- LEARN: ACCEPTED MISCONFIG @ roobet.com/_api/admin/*: admin routes (admin/users, admin/stats) exist on low-gate surface; return 401 Unauthorized; not behind Cloudflare 
- LEARN: ACCEPTED OTHER @ roobet.com/_api/affiliate/get: affiliate endpoint exists on low-gate surface; 401 auth-gated; potential IDOR target
- LEARN: ACCEPTED OTHER @ roobet.com/_api/settings/get: full internal config dump (IP, sessionId, restricted countries, withdraw flags, geo inference) — operational inte
- LEARN: ACCEPTED OTHER @ roobet.com/_api/tp-games/essentials: 9MB game catalog dump; internal S3 bucket reference; low severity
- LEARN: ACCEPTED OTHER @ roobet.com/_api/*: Full enumeration complete — 40 route candidates tested, exactly 6 live routes confirmed (settings/get 200, tp-games/essentia
- LEARN: ACCEPTED OTHER @ roobet.com auth/logout: Auth mechanism revealed — Express.js session cookies (connect.sid HttpOnly + userId non-HttpOnly + twofactorRequired). 
- LEARN: REJECTED MISCONFIG @ roobet.com: OAuth metadata endpoints return SPA shell (catch-all route), not JSON configuration
- LEARN: REJECTED MISCONFIG @ fs.roobet.com: GCS bucket ?list-type=2 redirects to fullstory.com; no object enumeration possible
- LEARN: REJECTED OTHER @ api.roobet.com: GraphQL endpoint blocked by Cloudflare bot management (403) without valid Origin/Referer/browser session
- LEARN: ACCEPTED MISCONFIG @ roobet.com: Remix catch-all route masks potential API endpoints under /api/* paths
- LEARN: PARKED api.roobet.com Cloudflare bypass: requires valid browser headers/session/turnstile to test
- LEARN: PARKED auth.roobet.com/account.roobet.com/admin.roobet.com: subdomains unresponsive; no attack surface confirmed
- LEARN: PARKED crash-gs.roobet.com unauthenticated socket: requires browser/WS tooling, HUMAN_ONLY
- LEARN: ACCEPTED MISCONFIG @ roobet.com/_api/admin/*: admin routes (admin/users, admin/stats) exist on low-gate surface; return 401 Unauthorized; not behind Cloudflare 
- LEARN: ACCEPTED OTHER @ roobet.com/_api/affiliate/get: affiliate endpoint exists on low-gate surface; 401 auth-gated; potential IDOR target
- LEARN: ACCEPTED OTHER @ roobet.com/_api/settings/get: full internal config dump (IP, sessionId, restricted countries, withdraw flags, geo inference) — operational inte
- LEARN: ACCEPTED OTHER @ roobet.com/_api/tp-games/essentials: 9MB game catalog dump; internal S3 bucket reference; low severity
- LEARN: ACCEPTED OTHER @ roobet.com/_api/*: Full enumeration complete — 40 route candidates tested, exactly 6 live routes confirmed (settings/get 200, tp-games/essentia
- LEARN: ACCEPTED OTHER @ roobet.com auth/logout: Auth mechanism revealed — Express.js session cookies (connect.sid HttpOnly + userId non-HttpOnly + twofactorRequired). 
- LEARN: REJECTED MISCONFIG @ roobet.com: OAuth metadata endpoints return SPA shell (catch-all route), not JSON configuration
- LEARN: REJECTED MISCONFIG @ fs.roobet.com: GCS bucket ?list-type=2 redirects to fullstory.com; no object enumeration possible
- LEARN: REJECTED OTHER @ api.roobet.com: GraphQL endpoint blocked by Cloudflare bot management (403) without valid Origin/Referer/browser session
- LEARN: ACCEPTED MISCONFIG @ roobet.com: Remix catch-all route masks potential API endpoints under /api/* paths
- LEARN: PARKED api.roobet.com Cloudflare bypass: requires valid browser headers/session/turnstile to test
- LEARN: PARKED auth.roobet.com/account.roobet.com/admin.roobet.com: subdomains unresponsive; no attack surface confirmed
- LEARN: PARKED crash-gs.roobet.com unauthenticated socket: requires browser/WS tooling, HUMAN_ONLY
