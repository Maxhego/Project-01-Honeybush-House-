# Optional GitHub Actions deployment

A **manual-only** workflow is provided at `.github/workflows/deploy.yml`. It does not run automatically on pushes. It has **not been executed or tested**.

## Prerequisites
1. Review [asset provenance](asset-provenance.md). The current `images/` folder contains eight replacement SVGs. Before redeployment, review and remove old raster objects at the destination and resolve affected cached copies; this workflow does not delete them.
2. Create a GitHub OIDC identity provider and a narrowly scoped AWS IAM role. Restrict the role trust policy to this exact repository and the intended branch.
3. Grant the role only the required S3 object upload/list permissions for the intended bucket and `cloudfront:CreateInvalidation` for the intended distribution.
4. Add GitHub Actions repository variables (Settings → Secrets and variables → Actions → Variables):
   - `AWS_ROLE_ARN` — role to assume via OIDC
   - `S3_BUCKET_NAME` — target S3 bucket name
   - `CLOUDFRONT_DISTRIBUTION_ID` — distribution to invalidate
5. Review the workflow and confirm the asset/deployment cleanup checklist before selecting Actions → Deploy Honeybush House to S3 → Run workflow. The required `asset_review_complete` input defaults to false; leave it false until that review is complete.

## Safety notes
- No long-lived AWS access keys are required or should be stored in GitHub.
- This workflow uploads site assets but does **not** delete remote S3 objects.
- Running it may incur S3, CloudFront and other AWS charges.
- The workflow is a prepared example, **not evidence of a working CI/CD pipeline** until the IAM configuration is completed and a deployment is successfully tested.
