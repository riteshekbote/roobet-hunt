## 2026-09-03 17:17:36 UTC [target] (model bigpickle)
[NEW] `fs.roobet.com` (34.8.116.253, non-Cloudflare GCP/GCS host, 200, serves FullStory `/s/fs.js`) — absent from inventory.
[NEW] `crash-gs.roobet.com` (Cloudflare, Crash game-server, wss/socket.io) — absent from inventory.
[CHANGED] `api.roobet.com` confirmed Cloudflare bot-managed: plain curl => 403 block; GraphQL WS ports 8087(product)/8088(admin) embedded in client bundle but NOT externally reachable (Cloudflare exposes only 443/8443).
[CHANGED] `roobet.com` is Remix/React SPA; all `/api/*` server-differentiables absent (200 SPA shell catch-all).
[PRIO] api.roobet.com,6.7,GRAPHQL_ADMIN_WSPORTS
[PRIO] fs.roobet.com,5.4,GCS_BUCKET_MISCONFIG
[PRIO] roobet.com,4.55,CLIENT_TOKEN_LEAK
[HYP] Exposed/internal GraphQL backend behind api.roobet.com with admin WS port 8088
class: MISCONFIG
asset: api.roobet.com:8088 (wss GraphQL-over-WebSocket); wss://api.roobet.com/
confidence: 55
reasoning: Client bundle embeds ROOBET_WS_GQL_PRODUCT_PORT=8087, ROOBET_WS_GQL_ADMIN_PORT=8088, ROOBET_WS_API_URL=wss://api.roobet.com/. A dedicated admin GraphQL port implies an admin-only schema. api.roobet.com is behind Cloudflare bot management (curl => 403 block), so WS/GQL surface needs a real turnstile-passing browser session.
evidence_needed: Reachable GraphQL-over-WS schema exposing admin mutations (user/bonus/wallet/role), or missing auth on the admin port.
verify_steps: In browser with turnstile passed: upgrade wss://api.roobet.com/ (and port 8088) with GraphQL subscription handshake; if 101 upgrade + introspection returns admin string/field names => exposed admin API. Read-only introspection only.
impact: ATO / privileged admin actions on money flows (bonuses, wallets, user management) => critical if reachable.
testability: AUTH_HELPED
[HYP] fs.roobet.com GCS bucket object exposure
class: MISCONFIG
asset: fs.roobet.com (GCP 34.8.116.253, GCS-backed)
confidence: 45
reasoning: fs.roobet.com is a Roobet-operated GCS host (x-goog-generation, MULTI_REGIONAL, UploadServer) serving /s/fs.js for FullStory. Root/listing 302 to www.eu1.fullstory.com. Non-Cloudflare GCP IP is a separate trust boundary; a misconfigured bucket could permit ListObjects or serve unintended objects.
evidence_needed: Bucket returns <ListBucketResult> or serves objects outside /s/ not intended to be public.
verify_steps: GET https://fs.roobet.com/?list-type=2&max-keys=1 (200 ListBucketResult vs 403 AccessDenied); GET https://fs.roobet.com/s/ then enumerate sibling object keys. Read-only.
impact: Info disclosure of internal static assets/scripts (possible private-bundle review or injected secrets) => medium.
testability: PASSIVE
[HYP] Commerce/event SDK & CMS token misconfiguration
class: OTHER
asset: roobet.com SPA bundle (ROOBET_* env leak)
confidence: 40
reasoning: Bundle exposes ROOBET_BETBY_BRAND_ID, ROOBET_PAYMENTIQ_MERCHANT_ID/ENV=sunpetal, Red Tiger launcher gserver-roobet.redtiger.cash, ContentStack delivery+preview tokens, VWO key. Delivery tokens are public-by-design; the preview token (csde...) MIGHT read unpublished draft CMS content. Launcher host is 3P redtiger.cash (out of scope).
evidence_needed: ContentStack preview API returns non-public draft content via preview token (read-only).
verify_steps: POST https://api.contentstack.io/… preview-locale query with the preview token. Read-only; low severity.
impact: Draft/confidential marketing-content disclosure => low; does not touch customer/financial/auth data (program-excluded).
testability: PASSIVE
[PARKED] Exposed GraphQL admin 8088: highest value but 8087/8088 verified NOT externally reachable (TCP to Cloudflare 443/8443 only open; ports refused) and 403 bot-block on HTTP => cannot confirm reachability passively. Kept as AUTH_HELPED for browser-phase; confidence dropped to 55.
[PARKED] Client token/CMS leak: ContentStack preview token is lower severity and touches no customer/financial data; delivery tokens are public keys => near-REJECTED class (public keys). Parked at 40.
[FINAL] fs.roobet.com GCS bucket misconfig: only fully PASSIVE-verifiable candidate; survivor.
[NEXT] PROBE: GET https://fs.roobet.com/?list-type=2&max-keys=1 then GET https://fs.roobet.com/s/ (compare 200 ListBucketResult vs 403); also GET https://fs.roobet.com/robots.txt content. If no 200 listing, escalate to browser-phase probe of wss://api.roobet.com/ GraphQL introspection (AUTH_HELPED).
[LEARN] REJECTED OTHER @ roobet.com bundle: delivered ContentStack tokens are public-by-design; not reportable. No delta in server surface from prior runs.
[RISK] roobet: 62 — real but gated surface (api.roobet.com Cloudflare/Turnstile bot-management blocks all scripted probes; GraphQL admin only via browser). Two new subdomains discovered; one testable passive lead (fs.roobet.com GCS). Engagement rules (max 1 rps, passive-first, no data modification, poc_required) complied with; no scanner POC runs.
