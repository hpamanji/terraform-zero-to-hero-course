# Provider Configuration Block
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
