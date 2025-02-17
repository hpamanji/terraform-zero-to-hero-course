# Terraform Providers

A provider in Terraform is a plugin that enables Terraform to interact with specific cloud services or APIs. Provider converts your Terraform configuration into API calls that the cloud provider understands.

Each provider comes with its own set of resources and data sources.
- Resources (e.g., AWS EC2, Azure VM, GCP Storage Bucket)
- Data Sources (fetches information about existing resources)

When we initialize Terraform with `terraform init` command, it downloads the required provider plugins from the Terraform Registry.

For example, Terraform AWS Provider allows you to create or manage AWS services like EC2, S3, Lambda, and more. 

### Setting up AWS Provider 

In your main.tf file, add:

```cmd
provider "aws" {
  region = "us-east-1"
}

resource "aws_s3_bucket" "first_bucket" {
  bucket = "first-bucket"
  acl    = "private"
}
```

To allow Terraform to communicate with AWS, configure credentials using AWS CLI:
```cmd
aws configure
```
