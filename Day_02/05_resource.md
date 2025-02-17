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
resource "aws_instance" "my_vm" {
  ami           = "ami-123456"
  instance_type = "t2.micro"
}
```

- ✔ Resource block defines what Terraform creates, updates, or deletes.
- ✔ Uses resource types (e.g., aws_instance, azurerm_virtual_machine).
- ✔ Each resource has arguments (e.g., ami, instance_type).
- ✔ Uses a unique resource name (my_vm) to track state.

---

## Understanding Resource Arguments

**Mandatory arguments:** Essential for resource creation (e.g., ami, instance_type).

**Optional arguments:** Can enhance resource behavior.

**Computed attributes:** Values assigned after resource creation (e.g., public_ip).
