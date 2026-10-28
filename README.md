# AWS Project 01 — Honeybush House

**Deploying a Static Website Using Amazon S3 and Amazon CloudFront**

## Project Overview

Honeybush House is a fictional South African tea brand website developed as a hands-on AWS cloud engineering portfolio project.

The objective was to build a responsive static website, store its files securely in Amazon S3, and distribute the website globally using Amazon CloudFront.

**Live Website:** https://d2f36m657zlp75.cloudfront.net/

## AWS Services Used

| Service | Purpose |
|---|---|
| Amazon S3 | Stores HTML, CSS, JavaScript, and image files |
| Amazon CloudFront | Delivers website content through a global content delivery network (CDN) |
| AWS IAM | Provides AWS identity and access management capabilities |
| CloudFront Origin Access Control (OAC) | Allows CloudFront to securely retrieve files from the private S3 bucket |

## Website Features

- Responsive website design
- Four pages: Home, Our Story, Our Teas, and Contact
- Tea product imagery and branding
- HTML, CSS, and JavaScript
- HTTPS delivery through CloudFront
- Private S3 origin

## Architecture

Visitor → Amazon CloudFront → Private Amazon S3 Bucket

Visitors request the website through CloudFront. CloudFront retrieves content from the S3 bucket when necessary and caches files at edge locations to improve delivery performance.

Origin Access Control restricts direct public access to the S3 bucket while allowing the configured CloudFront distribution to retrieve website files.

## Implementation Steps

1. Developed the website using HTML, CSS, and JavaScript.
2. Created an Amazon S3 bucket in the `eu-north-1` AWS Region.
3. Uploaded the website files and images to the bucket.
4. Kept S3 Block Public Access enabled.
5. Created a CloudFront distribution using the S3 bucket as its origin.
6. Enabled private bucket access for CloudFront.
7. Configured `index.html` as the default root object.
8. Corrected the S3 file structure so website files were located at the bucket root.
9. Created a CloudFront cache invalidation.
10. Tested the website pages through the CloudFront domain.

## Challenges and Troubleshooting

### AccessDenied Error

During deployment, CloudFront returned an `AccessDenied` error.

Investigation showed that the website files had initially been uploaded inside a parent folder rather than directly into the S3 bucket root.

**Resolution:** Uploaded the website files and images using the correct S3 object paths and invalidated the CloudFront cache.

### CloudFront Caching

CloudFront can temporarily serve cached responses after website files are changed.

**Resolution:** Used the CloudFront Invalidations feature to request fresh content.

## Testing

The following pages were tested through the CloudFront website:

- Home — `index.html`
- Our Story — `story.html`
- Our Teas — `teas.html`
- Contact — `contact.html`

The website was confirmed to load successfully after correcting the S3 object structure.

## Skills Demonstrated

- Amazon S3 object storage
- Static website deployment
- CloudFront CDN configuration
- Secure S3 origin access
- Basic AWS access control
- Troubleshooting HTTP access errors
- Cache invalidation
- AWS Console navigation
- HTML, CSS, and JavaScript deployment

## Cost Management

The project uses CloudFront pay-as-you-go billing and Amazon S3 storage.

CloudFront can be disabled when the demonstration is complete to stop serving public traffic. S3 storage and other applicable AWS charges may continue until the relevant resources are removed.

## Future Improvements

- Add a custom domain name
- Automate deployment with GitHub Actions
- Add infrastructure as code using AWS CloudFormation or Terraform
- Improve monitoring and cost alerts
- Add a functional contact form using serverless AWS services

## Project Status

**Deployed and tested — October 2026**

This project is part of a five-project AWS cloud engineering portfolio focused on developing practical cloud infrastructure and deployment skills.


## Architecture diagram and supporting documentation

- [Architecture diagram](docs/architecture.md) — Mermaid diagram of CloudFront, OAC and private S3
- [Testing and evidence checklist](docs/testing.md) — manual checks, reported outcomes and screenshot placeholders
- [Security and cost review](docs/security-and-cost.md) — access controls and budget verification
- [CloudFormation example](infra/README.md) — educational template for a **new** stack; not deployed
- [GitHub Actions deployment guide](docs/deployment-automation.md) — optional, manual-only workflow; not yet configured or run

### Repository completeness

The website source code is present. **The `images/` assets are still missing from GitHub**, so a clone will show missing images until those files are uploaded. Some image assets are AI-generated concepts. The contact form is demo-only and does not send messages.

### Deployment and automation status

The existing AWS site was deployed manually using the console. The infrastructure-as-code and GitHub Actions files are **prepared examples**, not proof that an automated deployment has been completed. Running the CloudFormation template would create separate potentially billable resources. The Actions workflow requires an explicitly configured, least-privilege AWS OIDC role and repository variables, and runs only when manually dispatched.
