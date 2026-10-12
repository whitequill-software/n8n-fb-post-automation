# SOP — Facebook Property Post Automation

**Status:** Recovery + production-readiness runbook. **Current documented state:** Python on scheduled GitHub Actions, **failing with a runtime error** (README); originally built in n8n. Owner: project maintainer.

## Purpose
Choose an authorized property image from Google Drive, create a property-grounded AI caption and publish it to a business Facebook Page through the Graph API.

## Before operating
- Only post images/content the business is licensed and authorized to publish. Confirm property facts, pricing, promotion validity and marketing compliance.
- Verify Drive access, LLM credentials, Facebook Page token/scopes, Graph API endpoint and GitHub Actions secrets.
- Keep a designated **approval step** before publishing any AI-generated factual property claims. The README currently describes automatic posting; a human-approval gate must be verified or added before production use.
- Do not place tokens, lead details, client documents or private Drive images in GitHub logs.

## Recovery procedure — current priority
1. **Pause scheduled publishing** while diagnosing the documented runtime failure to prevent unintended repeats.
2. Open the latest failed GitHub Actions run; record workflow/run URL, failed step, redacted traceback and timestamp.
3. Classify error: dependency/import, GitHub secret, Google auth, LLM model/response, Facebook Graph API permissions or media upload.
4. Fix the root cause on a test branch. Never paste credentials into an issue or commit.
5. Run a **dry-run** that selects an image and drafts text but does not call the Facebook publish endpoint. If no dry-run switch exists, implement one first.
6. Check caption against authorized project facts; approve in a controlled way.
7. Make one explicitly approved test publish; inspect post ID/content and reconcile run logs.
8. Re-enable scheduling only after a successful full workflow and a rollback/recovery plan.

## Expected operational flow (target)
1. Scheduled run starts, retrieves only approved Drive assets.
2. Retrieve current property knowledge; create grounded draft and retain input/source references for review.
3. Validate claims, compliance, media rights, length and prohibited content.
4. Human approves post; no approval means **no publishing**.
5. Publish once; persist idempotency key/post ID to avoid double posting on retry.
6. Log success/failure without secrets; alert on failure or missed schedule.

## Troubleshooting
| Symptom | Check | Resolution |
|---|---|---|
| Actions runtime exception | Failing step and traceback | Fix version/dependency/config; dry-run and regression test |
| Facebook permission/token error | Page token validity, scopes, expiry | Reauthorize through supported Meta flow; update secret store; test limited publish |
| Image fails to load | Drive permissions, MIME type, file ID | Verify approved asset access and media format |
| Wrong project info | Grounding source freshness and prompt | Stop publish; update verified source; require reapproval |
| Duplicate post | Retry paths and post ID history | Pause retries; reconcile published IDs; add idempotency state |
| No post despite successful run | API response/post ID and page | Verify result before declaring success; alert operator |

## Production acceptance — evidence required
- [ ] Root cause of current runtime failure documented and fixed.
- [ ] Safe dry-run mode and human approval gate proven.
- [ ] Token rotation/renewal and expiry monitoring documented.
- [ ] Posting idempotency and retry behavior tested.
- [ ] Business rules and compliance checks validated.
- [ ] Alerts, run logs and missed-execution checks in place.
- [ ] One controlled successful live publish, recorded post ID and rollback instructions.

**Do not represent this workflow as currently healthy until the runtime failure has been fixed and a production test passes.**
