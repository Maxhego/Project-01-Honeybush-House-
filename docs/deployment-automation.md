# Optional GitHub Actions deployment

A **manual-only** workflow is provided at `.github/workflows/deploy.yml`. It does not run automatically on pushes. It has **not been executed or tested**.

## Prerequisites
1. The repository's `images/` folder now includes the 20 website image files. Review the assets and filenames before any future deployment.
2. Create a GitHub OIDC identity provider and a narrowly scoped AWS IAM role. Restrict the role trust policy to this exact repository and the intended branch.
3. Grant the role only the required S3 object upload/list permissions for the intended bucket and `cloudfront:CreateInvalidation` for the intended distribution.
4. Add GitHub Actions repository variables (Settings → Secrets and variables → Actions → Variables):
   - `AWS_ROLE_ARN` — role to assume via OIDC
   - `S3_BUCKET_NAME` — target S3 bucket name
   - `CLOUDFRONT_DISTRIBUTION_ID` — distribution to invalidate
5. Review the workflow before manually choosing Actions → Deploy Honeybush House to S3 → Run workflow.

## Safety notes
- No long-lived AWS access keys are required or should be stored in GitHub.
- This workflow uploads site assets but does **not** delete remote S3 objects.
- Running it may incur S3, CloudFront and other AWS charges.
- The workflow is a prepared example, **not evidence of a working CI/CD pipeline** until the IAM configuration is completed and a deployment is successfully tested.
