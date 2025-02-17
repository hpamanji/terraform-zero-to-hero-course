# Multiple Provider Configurations using `alias`

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
