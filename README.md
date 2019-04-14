# Infrastructure code for static website with S3 and Cloudfront
This repository contains CloudFormation infrastructure code for creating static websites using S3 and Cloudfront. It :

1. Creates a CodeCommit repository to hold code for the static website.
2. Creates a CodeBuild project to continuously deploy on git push.
3. Creates the S3 bucket and Cloudfront distribution to host and front the website.
4. Creates the Route53 A and CNAME records for the domain of the website.