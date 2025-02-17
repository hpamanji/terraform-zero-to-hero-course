# Variables in Terraform

Variables in terraform helps us in making configurations dynamic

Instead of hardcoding values, use variables to make configurations reusable.

- Variables allow flexibility and customization.
- Use `var.<variable_name>` to reference them.
- Store default values in `variables.tf` or override in `terraform.tfvars`.

## Step 1: Declare Variables (variables.tf)

```cmd
variable "instance_type" {
  default = "t2.micro"
}
```

## Step 2: Use Variables (main.tf)

```cmd
resource "aws_instance" "my_vm" {
  ami           = "ami-0c55b159cbfafe1f0"
  instance_type = var.instance_type
}
```

## Step 3: Provide Values (terraform.tfvars)

```cmd
instance_type = "t3.medium"
```
