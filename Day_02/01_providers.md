# Terraform Providers

A provider in Terraform is a plugin that enables Terraform to interact with specific cloud services or APIs. 

Provider converts your Terraform configuration into API calls that the cloud provider understands.

Each provider comes with its own set of resources and data sources.
- Resources (e.g., AWS EC2, Azure VM, GCP Storage Bucket)
- Data Sources (fetches information about existing resources)

For example, Terraform AWS Provider allows you to create or manage AWS services like EC2, S3, Lambda, and more. 

When we initialize Terraform with `terraform init` command, the required provider plugins are downloaded from the [Terraform Registry](https://registry.terraform.io/browse/providers).

## Provider Configuration Block
Providers comes with its own configuration settings like region, or authentication details that must be set up before Terraform can manage resources on that cloud service/platform.

To configure a provider, add a provider block in your Terraform configuration file. 

In the example below, we are addding `aws provider` in our terraform configuration file (main.tf):

```cmd
provider "aws" {
  region = "us-east-1"
}

resource "aws_s3_bucket" "first_bucket" {
  bucket = "first-bucket"
  acl    = "private"
}
```

**Key Points:**

- The name in the block (`aws` in this example) refers to the provider.
- The arguments inside the block (like `region`) define settings specific to the provider.

`Note: To allow Terraform to communicate with AWS, configure credentials using AWS CLI:`
```cmd
aws configure
```

## Multiple Provider Configurations using `alias`

Let's say, we want to create multiple EC2 instances in different AWS regions. 

We can achieve this with one configuration file instead of multiple configurations for each region. 

We can define multiple provider blocks within a single configuration file, each referring to a different AWS region. Terraform allows us to do this using the `alias` argument, which helps differentiate between provider instances.

In the example below, we are Creating EC2 Instances in Two Regions. We have to explicitly specify the additional provider name(aws.west) otherwise the default provider will be refered.

```cmd
# Default AWS provider (us-east-1)
provider "aws" {
  region = "us-east-1"
}

# Additional AWS provider for the us-west-2 region
provider "aws" {
  alias  = "west"
  region = "us-west-2"
}

# EC2 instance in us-east-1 (default provider)
resource "aws_instance" "east_instance" {
  ami           = "ami-0c55b159cbfafe1f0"
  instance_type = "t2.micro"
}

# EC2 instance in us-west-2 (explicitly using aws.west provider)
resource "aws_instance" "west_instance" {
  provider      = aws.west
  ami           = "ami-0c55b159cbfafe1f0"
  instance_type = "t2.micro"
}
```

`Note: The default provider is used for all resources unless explicitly specified.`
