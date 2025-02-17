# Terraform Providers

A provider in Terraform is a plugin that enables Terraform to interact with specific cloud services or APIs. Provider converts your Terraform configuration into API calls that the cloud provider understands.

Each provider comes with its own set of resources and data sources.

When we initialize Terraform with `terraform init`, it downloads the required provider plugins from the Terraform Registry 

For example:
- The AWS provider manages EC2 instances, S3 buckets, and Lambda functions of AWS.
- The Azure provider handles Virtual Machines, Storage Accounts, and Resource Groups of Azure cloud.
- The GCP provider interacts with Compute Engine, Cloud Storage, and IAM of Google Cloud Platform.
- The Kubernetes provider helps manage Pods, Deployments, and Services in a kubernetes cluster.


For example, Terraform AWS Provider allows you to manage AWS services like EC2, S3, Lambda, and more. 

### Setting up AWS Provider 

In your main.tf file, add:

```cmd
provider "aws" {
  region = "us-east-1"
}
```

To allow Terraform to communicate with AWS, configure credentials using AWS CLI:
```cmd
aws configure
```
