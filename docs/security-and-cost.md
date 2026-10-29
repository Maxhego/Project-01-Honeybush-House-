# Security and cost review

The CloudFront demo is offline following the reported successful deployment. Current account settings, resource deletion and billing have not been independently verified. See the [evidence checklist](portfolio-evidence.md).

## Security configuration to verify
- S3 Block Public Access: enabled
- S3 Object Ownership: bucket owner enforced
- CloudFront origin: regular S3 REST endpoint
- Origin Access Control: enabled, with request signing
- Bucket policy: only the intended CloudFront distribution may read objects
- Viewer protocol: redirect HTTP to HTTPS
- No AWS credentials, tokens or private keys in this repository

## Cost considerations
The historical deployment used CloudFront pay-as-you-go and Amazon S3. A displayed **$0/month** is not a guarantee of zero usage charges. S3 storage and requests, CloudFront traffic and requests, and other optional services can incur charges.

Suggested manual steps:
1. Open AWS Billing and Cost Management.
2. Create a low AWS Budget threshold and email notification, if available.
3. Review Cost Explorer or Bills after deployment and testing.
4. Disable CloudFront when the public demonstration is no longer needed; note that S3 storage and previously accrued charges may remain.
5. If deleting resources later, confirm retention needs and remove resources deliberately.

**Not verified:** Whether a budget alert exists in the AWS account. Budget alerts do not automatically shut off services.
