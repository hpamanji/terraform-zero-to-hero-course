# Terraform State – Tracking Infrastructure

Terraform keeps track of infrastructure using a state file (terraform.tfstate).

### Why is Terraform State Important?
- Ensures Terraform knows which resources exist.
- Prevents duplicate resource creation.
- Helps Terraform detect and apply changes.

### How to View the State File?
```cmd
terraform show
```

### Best Practice: Store State Remotely (AWS S3 Backend)
```cmd
terraform {
  backend "s3" {
    bucket = "my-terraform-state"
    key    = "terraform.tfstate"
    region = "us-east-1"
  }
}
```

### Key Points:
- Local state is fine for testing, but use remote storage for production.
- Supports S3, Terraform Cloud, Consul, Azure Storage, and more.
- Enables team collaboration and locking to prevent conflicts.
