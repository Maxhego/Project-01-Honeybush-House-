# CloudFormation example (not deployed)

`cloudformation.yaml` describes a **new**, separate private S3 bucket, CloudFront OAC, bucket policy and distribution. It is educational infrastructure-as-code; the current Honeybush House site was configured manually through the AWS Console.

**Do not deploy this template without reviewing it.** It will create additional AWS resources and may incur charges. It does not import, modify or automatically adopt the existing S3 bucket or CloudFront distribution.

The template has not been deployed or validated against your AWS account. To test it later, use CloudFormation's validation and change-set workflow, inspect the proposed resources and costs, then deploy only after approval. The newly created bucket would initially be empty; website files would need to be uploaded separately.
