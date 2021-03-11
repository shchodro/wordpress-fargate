# Wordpress on Fargate

This terraform example demonstrates how to run a scalable wordpress site. In this exmaple, serverless technologies are used as much as possible. Hence, website is running on fargate and are Aurora serverless is used as DB.

## AWS Services

- Fargate - for computing
- Aurora Serverless - for database
- EFS (Elastic File System) - for persistent data storage
- Cloudfront - CDN

## Terraform setup

## Initialize terraform environment

```
terraform init -backend-config="bucket=<BUCKET_NAME>" -backend-config="profile=<AWS_PROFILE>" -backend-config="region=<AWS_REGION>"
```

### Create environment

```
  AWS_SDK_LOAD_CONFIG=1 \
  TF_VAR_site_domain=<PUBLIC_DOMAIN> \
  TF_VAR_public_alb_domain=<INTERNAL_DOMAIN_FOR_ALB> \
  TF_VAR_db_master_username=<DB_MASTER_USERNAME> \
  TF_VAR_db_master_password="<DB_MASTER_PASSWORD>" \
  AWS_PROFILE=<AWS_PROFILE> \
  AWS_DEFAULT_REGION=<AWS_REGION> \
  terraform apply
```

### Tear down

```
  AWS_SDK_LOAD_CONFIG=1 \
  TF_VAR_site_domain=<PUBLIC_DOMAIN> \
  TF_VAR_public_alb_domain=<INTERNAL_DOMAIN_FOR_ALB> \
  TF_VAR_db_master_username=<DB_MASTER_USERNAME> \
  TF_VAR_db_master_password="<DB_MASTER_PASSWORD>" \
  AWS_PROFILE=<AWS_PROFILE> \
  AWS_DEFAULT_REGION=<AWS_REGION> \
  terraform destroy
```

p.s. Instead of environment variables, you can obviously use .tfvar files for assigning values to terraform variables.
