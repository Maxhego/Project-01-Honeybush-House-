# Portfolio evidence checklist

Review date: 30 October 2026. The repository contains source, architecture documentation, an example CloudFormation template and a manual-only Actions workflow. Original image assets are missing. Nine user-supplied desktop screenshots were subsequently added to the [gallery](screenshots/README.md); hosting environment and capture time are unverified. The Actions run history returned zero runs at review.

The CloudFront demo remains offline. Do not enable it merely to make the README appear complete.

## Priority additions

Suggested paths below are future filenames, not links to existing evidence.

| Priority | Missing item | Suggested path or link | What it establishes |
|---|---|---|---|
| 1 | Original website images and asset-origin note | `images/` and `images/README.md` | A clone can reproduce the visual site; distinguish AI-generated concepts from other assets and record usage rights |
| Supplied | Desktop captures covering all four pages | [Screenshot gallery](screenshots/README.md) | Visible page appearance; does not establish AWS deployment provenance |
| 1 | Mobile capture with viewport recorded | `docs/screenshots/home-mobile.png` | Visible layout at the stated size; does not establish all-device compatibility |
| 2 | S3 Objects capture | `docs/screenshots/s3-root-objects.png` | Correct root-level keys, including `index.html`, illustrating the troubleshooting resolution |
| 2 | CloudFront origin, OAC and default root object | `docs/screenshots/cloudfront-origin.png`, `cloudfront-root-object.png` | Documented connection between the distribution and private S3 origin |
| 2 | Block Public Access and sanitized bucket policy | `docs/screenshots/s3-private-access.png` | Access settings and distribution-scoped read policy |
| 2 | Completed cache invalidation | `docs/screenshots/invalidation-completed.png` | The invalidation step completed; not proof of page correctness |
| 2 | Dated manual test record or sanitized HTTP output | Extend `docs/testing.md` | Actual page results, HTTPS behavior and blocked anonymous S3 reads |
| 2 | Disabled distribution capture | `docs/screenshots/cloudfront-disabled.png` | Offline state at capture time; not proof that every resource was deleted |
| 3 | Billing and budget evidence, if available | Sanitized record linked from `docs/security-and-cost.md` | Actual cost period and alert configuration; no zero-cost claim without evidence |
| 3 | Successful automation run, only after it is tested | Permanent GitHub Actions run URL | A specific workflow executed successfully; currently absent |

## Captions and provenance

For each capture, record the date, environment (historical AWS deployment, current AWS settings, or local preview), page/resource, relevant viewport and what the capture demonstrates. Redact credentials, tokens, account identifiers and private billing/contact details.

Use existing historical captures if available. A screenshot made locally today must not be presented as proof of the October AWS deployment. If historical evidence cannot be recovered, leave the result labeled user-reported. Do not fabricate before/after screenshots or HTTP outputs.

The homepage screenshot is embedded in the README and all captures are linked from the test record. Add only links that resolve to committed files. A short captioned walkthrough video can be useful, but is optional.

## Links to retain or add

- Retain the [offline-status commit](https://github.com/Maxhego/Project-01-Honeybush-House-/commit/8c7af193b347e74964fb585abcc7b3482a2c8af0) as a historical status record.
- Keep the historical CloudFront domain explicitly marked offline; do not label it “Live demo”.
- Link actual screenshot files, test records and any future successful Actions run directly.
- A LinkedIn/contact link can be added by the owner if desired; no personal URL is assumed.
- A custom domain is not required to explain this project.

## Review boundary

This review inspected repository documentation, site references, infrastructure/workflow source and GitHub Actions run history. It did not access the AWS account, reactivate resources, rerun deployment tests, validate the template in AWS or measure performance. The existing architecture diagram describes intent and reported implementation; it is not deployment evidence.
