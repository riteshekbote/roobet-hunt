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
