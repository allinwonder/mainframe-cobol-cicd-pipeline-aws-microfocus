# CloudFormation Templates

## Prerequsists

1. AWS Account
2. AWSCLI

## How to Deplooy?

1. Create an S3 bucket for storing the templates

use the following command to create an s3 bucket, you need to replace the `BUCKET_NANE` with a choice of your bucket name
```
aws s3 mb BUCKET_NAME
```

2. Upload CloudFormation Templates

use the following command to upload template to s3 bucket, you need to replace the `BUCKET_NANE` with the bucket name you use in previous command
```
for f in `ls -1 *.yaml`; do aws s3 cp $f s3://BUCKET_NAME/; done
```

3. Deploy CloudFormation Stack


use the following command to deploy CloudFormation stacks, you need to replace the `BUCKET_NANE` with the bucket name you use in previous command
```
aws cloudformation deploy --stack-name mainframe-cobol-cicd-pipeline-aws-microfocus --template-file master.yaml --parameter-overrides BucketName=BUCKET_NAME --capabilities CAPABILITY_IAM
```
