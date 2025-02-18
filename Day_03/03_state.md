# Terraform State – Tracking Infrastructure

Terraform keeps track of infrastructure using a state file (terraform.tfstate).

### What is Terraform State?

Terraform state (terraform.tfstate) is a JSON file that maps resources in your configuration to real-world infrastructure.

It tracks metadata, dependencies, and resource attributes.

### Why is Terraform State Important?
- Enables Terraform to determine what changes need to be made during terraform apply.
- Tracks resource dependencies and attributes.
- Ensures idempotency (applying the same configuration multiple times results in the same state).

### How to View the State File?
```cmd
terraform show

#state file structure - Contains resource mappings, metadata, and outputs.

{
  "version": 4,
  "terraform_version": "1.3.0",
  "resources": [
    {
      "mode": "managed",
      "type": "aws_instance",
      "name": "web",
      "provider": "provider.aws",
      "instances": [
        {
          "attributes": {
            "ami": "ami-123456",
            "instance_type": "t2.micro"
          }
        }
      ]
    }
  ]
}
```

---

2. Local vs Remote State
Local State
Default behavior: State is stored locally in a terraform.tfstate file.

Pros:

Simple to use.

No additional setup required.

Cons:

Not suitable for team collaboration.

Risk of losing state file.

Remote State
State is stored in a remote backend (e.g., S3, Terraform Cloud).

Pros:

Enables team collaboration.

Provides state locking and versioning.

Cons:

Requires additional setup.


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

