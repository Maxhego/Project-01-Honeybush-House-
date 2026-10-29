# Test plan and evidence

## Reported during the guided deployment
- The user reported that the homepage and all four pages loaded after uploading files at the S3 bucket root and invalidating CloudFront.
- The `AccessDenied` issue was encountered and subsequently reported resolved.

These are **user-reported results**, not independently recorded automated tests.

## Current status

**CloudFront is offline; the distribution was disabled after the successful demonstration.** The checklist below is a plan for a future authorized deployment, not a set of tests run during this review. Historical page-load results above remain user-reported. No automated test results or screenshot files are committed.

Local checks can cover navigation, layout and the demo form once the missing image assets are restored; they cannot verify HTTPS delivery or private S3 access. For each executed check, record date, environment, expected result, actual result and a capture or output link. Leave unexecuted checks pending.

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
1. Desktop homepage and product page
2. Mobile homepage
3. S3 Objects list showing `index.html` at bucket root
4. CloudFront general settings showing origin and default root object
5. CloudFront invalidation marked Completed

**Never include AWS access keys, secret values, session tokens or private account details in screenshots.**

## Troubleshooting note
An initial 403 AccessDenied response was observed when website files were nested under `Honeybush-House-Project01-FRESH/`. Moving the website contents to the bucket root and completing a CloudFront invalidation resolved the issue according to the user's browser test.
