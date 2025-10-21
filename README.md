# S3 Static Website (CLF-C02 – Day 1)
Deployed an S3 static website with public bucket policy and website endpoint.

**Live site:** http://clif-static-site.s3-website-us-east-1.amazonaws.com  
**Skills:** S3, Static Hosting, Bucket Policy, Troubleshooting 403/404
Live site: http://clif-static-site.s3-website-us-east-1.amazonaws.com
## What I built
A public S3 static website with proper bucket policy and website endpoint.

## How to deploy (mini runbook)
1) Create bucket (Region us-east-1), disable “Block all public access”.
2) Properties → Static website hosting → index document `index.html`.
3) Upload `index.html` (Content-Type: `text/html`).
4) Bucket policy:
```json
{
  "Version": "2012-10-17",
  "Statement": [{
    "Sid": "PublicReadGetObject",
    "Effect": "Allow",
    "Principal": "*",
    "Action": "s3:GetObject",
    "Resource": "arn:aws:s3:::clif-static-site/*"
  }]
}
## Troubleshooting
- **403 AccessDenied** → Turn off Block Public Access + add bucket policy.
- **404 NoSuchKey** → Ensure the file is named exactly `index.html` (lowercase).
- **Wrong content-type** → Set `text/html` on the object metadata.

## Cost
Free-tier friendly (S3 storage + GET requests); delete bucket to stop charges.
