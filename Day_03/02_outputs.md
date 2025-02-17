# Outputs - Extracting Useful Information

Terraform outputs allow us to extract key values after deployment.

- Helps fetch key resource information (e.g., IP addresses, ARNs).
- Use terraform output to view output values after deployment.
- Useful for automation scripts and CI/CD pipelines.

Example: Retrieve EC2 Instance Public IP (outputs.tf)

```cmd
output "instance_public_ip" {
  description = "Public IP Adress of AWS Instance"
  value = aws_instance.my_vm.public_ip
}
```
