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
