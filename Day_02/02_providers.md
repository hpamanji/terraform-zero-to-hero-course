# Terraform Providers

A provider in Terraform is a plugin that enables Terraform to interact with specific cloud services or APIs. Terraform Supports multiple providers (AWS, Azure, Kubernetes, etc.).

Provider converts your Terraform configuration into API calls that the defined cloud provider understands.

Each provider requires authentication (via environment variables, IAM roles, etc.).

Each provider comes with its own set of resources and data sources.
- Resources (e.g., AWS EC2, Azure VM, GCP Storage Bucket)
- Data Sources (fetches information about existing resources)

For example, Terraform AWS Provider allows you to create or manage AWS services like EC2, S3, Lambda, and more. 

`Note: When we initialize Terraform with terraform init command, the required provider plugins are downloaded from the [Terraform Registry](https://registry.terraform.io/browse/providers).`
