## REPOSCAN 2026-09-03 17:14:49 UTC
TARGET_ORG not configured for roobet; skipping public-org deep scan.
## REPOSCAN 2026-09-03 19:59:29 UTC
TARGET_ORG not configured for roobet; skipping public-org deep scan.
## REPOSCAN 2026-09-03 22:29:49 UTC
TARGET_ORG not configured for roobet; skipping public-org deep scan.
## REPOSCAN 2026-09-04 00:27:20 UTC
[HYP] No findings — zero candidate repos to audit
class: OTHER
asset: github.com/ROOBET
confidence: 100
reasoning: GitHub org ROOBET has 0 public repositories. No source code is exposed.
impact: N/A
verify_steps: curl -s "https://api.github.com/orgs/ROOBET" | jq '.public_repos' → 0
TARGET_ORG not configured for roobet; skipping public-org deep scan.
## REPOSCAN 2026-09-04 05:07:46 UTC
TARGET_ORG not configured for roobet; skipping public-org deep scan.
## REPOSCAN 2026-09-04 09:46:13 UTC
TARGET_ORG not configured for roobet; skipping public-org deep scan.
## REPOSCAN 2026-09-04 14:07:36 UTC
TARGET_ORG not configured for roobet; skipping public-org deep scan.
## REPOSCAN 2026-09-04 17:42:16 UTC
TARGET_ORG not configured for roobet; skipping public-org deep scan.
## REPOSCAN 2026-09-04 19:57:14 UTC
TARGET_ORG not configured for roobet; skipping public-org deep scan.
## REPOSCAN 2026-09-04 22:16:54 UTC
TARGET_ORG not configured for roobet; skipping public-org deep scan.
## REPOSCAN 2026-09-05 00:12:48 UTC
TARGET_ORG not configured for roobet; skipping public-org deep scan.
## REPOSCAN 2026-09-05 04:41:39 UTC
TARGET_ORG not configured for roobet; skipping public-org deep scan.
## REPOSCAN 2026-09-05 08:41:11 UTC
[HYP] No Roobet GitHub org configured — zero candidate repos to audit
class: OTHER
asset: cands.txt / scope.yml
confidence: 100
reasoning: |
impact: N/A — no source code to audit; finding documents absence of configured targets
verify_steps: |
TARGET_ORG not configured for roobet; skipping public-org deep scan.
## REPOSCAN 2026-09-05 12:08:38 UTC
TARGET_ORG not configured for roobet; skipping public-org deep scan.
## REPOSCAN 2026-09-05 15:24:05 UTC
TARGET_ORG not configured for roobet; skipping public-org deep scan.
## REPOSCAN 2026-09-05 17:39:14 UTC
[HYP] No source code available — reposcan null run
class: OTHER
asset: cands.txt / scope.yml
confidence: 100
reasoning: cands.txt contains "no org candidates"; scope.yml has github_orgs: none-configured; GitHub org ROOBET has 0 public repos. No source code exists to audit for secrets, hardcoded creds, or insecure patterns.
impact: N/A
verify_steps: |
TARGET_ORG not configured for roobet; skipping public-org deep scan.
## REPOSCAN 2026-09-05 19:33:02 UTC
[HYP] No source code to audit — GitHub org ROOBET has zero public repos
class: OTHER
asset: github.com/ROOBET (org ID 46298934)
confidence: 100
reasoning: |
impact: N/A — absence of exposed source reduces attack surface but prevents this scan vector
verify_steps: |
TARGET_ORG not configured for roobet; skipping public-org deep scan.
## REPOSCAN 2026-09-05 21:43:33 UTC
[HYP] (none — no candidates)
class: N/A
asset: N/A
confidence: 0
reasoning: Roobet has zero public GitHub repos. All 122 search hits are third-party community tools, not the org's own code. No source-code secrets, hardcoded creds, or insecure patterns can be identified from org-owned repos.
impact: N/A
verify_steps: N/A — no repos to clone/scan
TARGET_ORG not configured for roobet; skipping public-org deep scan.
## REPOSCAN 2026-09-05 23:42:47 UTC
TARGET_ORG not configured for roobet; skipping public-org deep scan.
## REPOSCAN 2026-09-06 04:04:23 UTC
TARGET_ORG not configured for roobet; skipping public-org deep scan.
## REPOSCAN 2026-09-06 08:44:28 UTC
TARGET_ORG not configured for roobet; skipping public-org deep scan.
## REPOSCAN 2026-09-06 12:47:19 UTC
[HYP] Reposcan: No public org candidates configured
class: OTHER
asset: roobet-hunt/cands.txt
confidence: 100
reasoning: cands.txt contains "no org candidates". scope.yml lists github_orgs: [none-configured]. reposcan-raw/summary.txt confirms "TARGET_ORG not configured for roobet; skipping public-org deep scan." No public GitHub repos were cloned, so zero source-code artifacts exist to grep for AKIA, AIza, ghp_, sk_live_, private keys, passwords, api_keys, secrets, tokens, client_secrets, S3 buckets, GCS URLs, or Azure endpoints.
impact: None (informational)
verify_steps: 1) Confirm roobet has no public GitHub org at github.com/roobet (or the configured org name). 2) If an org exists, populate cands.txt with repo URLs and re-run reposcan.
TARGET_ORG not configured for roobet; skipping public-org deep scan.
## REPOSCAN 2026-09-06 16:06:56 UTC
TARGET_ORG not configured for roobet; skipping public-org deep scan.
## REPOSCAN 2026-09-06 18:25:07 UTC
TARGET_ORG not configured for roobet; skipping public-org deep scan.
## REPOSCAN 2026-09-06 20:49:22 UTC
TARGET_ORG not configured for roobet; skipping public-org deep scan.
## REPOSCAN 2026-09-06 22:50:24 UTC
[HYP] No findings
class: N/A
asset: N/A
confidence: N/A
reasoning: No Roobet-owned public GitHub repositories exist. All search results are third-party community projects (predictors, scrapers, analytics tools) which are not the org's own code and therefore out of scope per the bounty program rules.
impact: N/A
verify_steps: N/A
TARGET_ORG not configured for roobet; skipping public-org deep scan.
## REPOSCAN 2026-09-07 00:49:00 UTC
TARGET_ORG not configured for roobet; skipping public-org deep scan.
## REPOSCAN 2026-09-07 05:53:38 UTC
TARGET_ORG not configured for roobet; skipping public-org deep scan.
## REPOSCAN 2026-09-07 12:07:47 UTC
TARGET_ORG not configured for roobet; skipping public-org deep scan.
## REPOSCAN 2026-09-07 17:46:59 UTC
TARGET_ORG not configured for roobet; skipping public-org deep scan.
## REPOSCAN 2026-09-07 21:23:25 UTC
TARGET_ORG not configured for roobet; skipping public-org deep scan.
## REPOSCAN 2026-09-07 23:47:04 UTC
[HYP] N/A — no candidate repos to audit
class: N/A
asset: N/A
confidence: 100
reasoning: cands.txt = "no org candidates"; scope.yml github_orgs = none-configured; no official Roobet org exists on GitHub
impact: N/A
verify_steps: Verify Roobet has no public GitHub org; add one to github_orgs if discovered
TARGET_ORG not configured for roobet; skipping public-org deep scan.
## REPOSCAN 2026-09-08 04:02:19 UTC
TARGET_ORG not configured for roobet; skipping public-org deep scan.
## REPOSCAN 2026-09-08 08:55:50 UTC
TARGET_ORG not configured for roobet; skipping public-org deep scan.
## REPOSCAN 2026-09-08 13:29:03 UTC
TARGET_ORG not configured for roobet; skipping public-org deep scan.
## REPOSCAN 2026-09-08 17:30:40 UTC
TARGET_ORG not configured for roobet; skipping public-org deep scan.
## REPOSCAN 2026-09-08 20:19:05 UTC
TARGET_ORG not configured for roobet; skipping public-org deep scan.
## REPOSCAN 2026-09-08 22:46:28 UTC
[HYP] N/A — No org-owned repos found
class: N/A
asset: N/A
confidence: N/A
reasoning: Roobet has no public GitHub organization. All discovered repos are third-party/unofficial. The bug bounty program at bugs.olivermaicher.eu does not include public source code review as an in-scope attack vector — scope is the live platform.
impact: N/A
verify_steps: N/A
TARGET_ORG not configured for roobet; skipping public-org deep scan.
## REPOSCAN 2026-09-09 01:10:54 UTC
TARGET_ORG not configured for roobet; skipping public-org deep scan.
## REPOSCAN 2026-09-09 06:07:52 UTC
[HYP] <none>
TARGET_ORG not configured for roobet; skipping public-org deep scan.
## REPOSCAN 2026-09-09 11:34:37 UTC
TARGET_ORG not configured for roobet; skipping public-org deep scan.
