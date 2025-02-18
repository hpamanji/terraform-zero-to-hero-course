# Variables in Terraform

Terraform variables help make configurations dynamic and reusable, so we don't have to hardcode values.

- Variables allow flexibility and customization.
- Use `var.<variable_name>` to reference them.
- Store default values in `variables.tf` or override in `terraform.tfvars`.

### Step 1: Declare Variables (variables.tf)

```cmd
variable "instance_type" {
  default = "t2.micro"
}
```
This defines a variable with a default value as  t2.micro.

### Step 2: Use Variables (main.tf)

```cmd
resource "aws_instance" "my_vm" {
  ami           = "ami-0c55b159cbfafe1f0"
  instance_type = var.instance_type
}
```
Instead of hardcoding "t2.micro", we use var.instance_type.

### Step 3: Provide Values (terraform.tfvars)
We can override the default value by defining a different value in terraform.tfvars.
```cmd
instance_type = "t3.medium"
```
Now, when Terraform runs, it will use t3.medium instead of t2.micro.
