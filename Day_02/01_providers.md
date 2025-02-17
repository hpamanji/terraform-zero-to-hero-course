# Terraform Providers

A provider in Terraform is a plugin that enables Terraform to manage specific cloud services or APIs. Provider converts your Terraform configuration into API calls that the cloud provider understands.
Each provider comes with its own set of resources and data sources.
When you initialize Terraform (terraform init), it downloads the required provider plugins from the Terraform Registry 

For example:
- The AWS provider manages EC2 instances, S3 buckets, and Lambda functions of AWS.
- The Azure provider handles Virtual Machines, Storage Accounts, and Resource Groups of Azure cloud.
- The GCP provider interacts with Compute Engine, Cloud Storage, and IAM of Google Cloud Platform.
- The Kubernetes provider helps manage Pods, Deployments, and Services in a kubernetes cluster.

To use AWS with Terraform, define the AWS provider as below:

```cmd
provider "aws" {
  region = "us-east-1"
}
```

To use Azure, define the Azure provider as below:

```cmd
provider "azurerm" {
  features {}
}
```

For Google Cloud, use the GCP provider:

```cmd
provider "google" {
  project = "my-gcp-project"
  region  = "us-central1"
}
```

For Kubernetes, use the Kubernetes provider:

```cmd
provider "kubernetes" {
  config_path = "~/.kube/config"
}
```
