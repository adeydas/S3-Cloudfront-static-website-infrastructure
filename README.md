# Infrastructure code for static website with S3 and Cloudfront
This repository contains CloudFormation infrastructure code for creating static websites using S3 and Cloudfront. It :

1. Creates a CodeCommit repository to hold code for the static website.
2. Creates a CodeBuild project to continuously deploy on git push.
3. Creates the S3 bucket and Cloudfront distribution to host and front the website.
4. Creates the Route53 A and CNAME records for the domain of the website.

You will need:

1. A Route53 hosted zone for your domain.
2. To create a buildspec.yml that tells CodeBuild how to build and deploys your static website contents to the S3 bucket. Could be something as simple as this:
````yml
version: 0.2

phases:
  install:
    commands:
      - gem install bundler jekyll
      - gem install jekyll-last-modified-at
      - gem install minima
  build:
    commands:
      - jekyll build
      - aws s3 sync _site/ s3://abhishek.deydas.name
      - aws cloudfront create-invalidation --distribution-id E1PRO30G7BA7NW --paths "/*"

````
3. Some time and patience :).