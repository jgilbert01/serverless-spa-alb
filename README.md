# serverless-spa-alb

Serverless plugin to configure S3, ALB and Route53 for a private SPA site.

This approach is useful when CloudFront is not permitted. It sets up API Gateway as a proxy to S3.

* Creates S3 bucket
* Connects to an ALB _(unless apig:false)_
* Creates Route 53 RecordSet _(when hostedZoneId is provided)_

> This plugin is designed to work in conjunction with the [_serverless-spa-deploy_](https://github.com/DanteInc/serverless-spa-deploy) plugin.

## serverless.yml

> Optional settings are commented out

```
plugins:
  - serverless-spa-deploy
  - serverless-spa-alb

custom:
  # partition: aws-us-gov
  spa:
    websiteBucketNameOutputRef: SpaBucketName
    acl: private
    files: # per serverless-spa-deploy
      ...
  alb: # false
    hostedZoneId: ZZZZZZZZZZZZZZZZZZZZ
    domainName: example.com
    acmCertificateArn: arn:aws:acm:us-east-1:0123456789:certificate/xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx
    # webACLId: xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx
    # vpcEndpointId: xxxxxx
```
