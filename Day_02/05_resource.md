# Understanding Terraform Resources

What is a Terraform Resource?

A resource in Terraform represents an infrastructure object (e.g., EC2 instance, S3 bucket, VPC, etc.). Resources are defined using the resource block.

Resource Block Syntax:

```cmd
resource "<provider>_<type>" "<name>" {
  # Configuration settings
}
```

Here is an example resource: Creating an AWS EC2 Instance
```cmd
resource "aws_instance" "example" {
  ami           = "ami-123456"
  instance_type = "t2.micro"
}
```
