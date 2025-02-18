# Importing Existing Resources

### Why Import Resources?
- Bring existing infrastructure under Terraform management.
- Avoid recreating resources.

### Steps to Import Resources
1. Add the resource to your configuration:
   ```hcl
   resource "aws_instance" "web" {
     instance_type = "t2.micro"
   }

2. Use terraform import to map the resource:
```cmd
terraform import aws_instance.web i-1234567890abcdef0
```

3. Verify the import:

```cmd
terraform show
```
