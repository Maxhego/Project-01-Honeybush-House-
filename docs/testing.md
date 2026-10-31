# Test plan and evidence

## Reported during the guided deployment
- The user reported that the homepage and all four pages loaded after uploading files at the S3 bucket root and invalidating CloudFront.
- The `AccessDenied` issue was encountered and subsequently reported resolved.

These are **user-reported results**, not independently recorded automated tests.

## Current status

**CloudFront is offline; the distribution was disabled after the successful demonstration.** The checklist below is a plan for a future authorized deployment, not a set of tests run during this review. Historical page-load results above remain user-reported. Earlier user-supplied desktop screenshots have been withdrawn from the current tree because they reproduce imagery with unverified rights; see [capture notes](screenshots/README.md). Their hosting environment is unverified; no automated test results are committed.

Local checks can cover navigation, layout and the demo form using the included `images/` assets; they cannot verify HTTPS delivery or private S3 access. For each executed check, record date, environment, expected result, actual result and a capture or output link. Leave unexecuted checks pending.

See the [portfolio evidence checklist](portfolio-evidence.md) for prioritized captures and provenance requirements.

## Pending manual test checklist (requires an active deployment)
- [ ] Home: https://d2f36m657zlp75.cloudfront.net/
- [ ] Story: https://d2f36m657zlp75.cloudfront.net/story.html
- [ ] Teas: https://d2f36m657zlp75.cloudfront.net/teas.html
- [ ] Contact: https://d2f36m657zlp75.cloudfront.net/contact.html
- [ ] All images load (including background images)
- [ ] Navigation links work on desktop
- [ ] Navigation and layout work on a narrow mobile viewport
- [ ] HTTPS certificate shows no browser warning
- [ ] Contact form displays its demo-only message and does not transmit data
- [ ] Direct public S3 object URL is blocked (expected with private bucket)
- [ ] Confirm S3 Block Public Access and OAC in AWS Console

## Screenshots to add
Save sanitized screenshots under `docs/screenshots/`:
1. Fresh desktop homepage and product page using replacement SVGs — pending; label as local unless actually hosted
2. Mobile homepage
3. S3 Objects list showing `index.html` at bucket root
4. CloudFront general settings showing origin and default root object
5. CloudFront invalidation marked Completed

**Never include AWS access keys, secret values, session tokens or private account details in screenshots.**

## Troubleshooting note
An initial 403 AccessDenied response was observed when website files were nested under `Honeybush-House-Project01-FRESH/`. Moving the website contents to the bucket root and completing a CloudFront invalidation resolved the issue according to the user's browser test.

## Desktop visual evidence received 30 October 2026

Nine user-supplied captures previously showed Home, Story, Teas and Contact. They have been removed from the current tree because they reproduce the retired raster assets; see [historical inventory](screenshots/README.md). They never established AWS settings, HTTPS or complete browser behavior.

## Repository asset check — 30 October 2026

Historical check: the folder contained 20 raster files and site references resolved. That did not establish asset origins or usage rights. On 31 October these files were removed from the current tree and replaced by eight AI-assisted SVG illustrations; see [asset record](asset-provenance.md). The changed version has not been redeployed to AWS. Fresh browser validation and screenshots are separate from the historical deployment report.

## Replacement-source checks — 31 October 2026

- Passed: all 16 image references in the four HTML pages and CSS resolve to the eight replacement SVG files.
- Passed: all eight SVGs parse as XML and rasterize successfully; a rendered contact sheet was visually inspected.
- Passed: replacement SVGs contain no scripts, embedded raster images or external resource references.
- Passed: workflow YAML parses; the manual asset-review input defaults to false and gates the deployment job.
- Full-page browser layout checks were attempted but could not run because the local Playwright browser executable was unavailable. Fresh desktop/mobile browser checks remain pending.
- No AWS access, deployment, old-object cleanup, cache invalidation, or Git-history purge was performed.
