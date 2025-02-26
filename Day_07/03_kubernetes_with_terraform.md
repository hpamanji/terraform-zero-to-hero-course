# Why Terraform for Kubernetes?

Terraform simplifies the management of Kubernetes clusters by:

- Automating cluster creation and configuration.

- Managing Kubernetes resources (e.g., deployments, services) as code.

- Integrating with cloud providers for seamless cluster provisioning.

### Managing a Kubernetes Cluster

Here’s how you can create a Kubernetes cluster on AWS (EKS) and deploy a sample application:


### Create an EKS Cluster
module "eks" {
  source  = "terraform-aws-modules/eks/aws"
  version = "~> 18.0"

  cluster_name    = "my-eks-cluster"
  cluster_version = "1.21"

  vpc_id          = aws_vpc.example.id
  subnets         = [aws_subnet.example.id]

  worker_groups = [
    {
      instance_type = "t2.medium"
      asg_max_size  = 3
    }
  ]
}

### Deploy a Kubernetes Application

provider "kubernetes" {
  host                   = module.eks.cluster_endpoint
  cluster_ca_certificate = base64decode(module.eks.cluster_certificate_authority_data)
  token                  = module.eks.cluster_auth_token
}

resource "kubernetes_deployment" "example" {
  metadata {
    name = "example-deployment"
  }

  spec {
    replicas = 3

    selector {
      match_labels = {
        app = "example"
      }
    }

    template {
      metadata {
        labels = {
          app = "example"
        }
      }

      spec {
        container {
          name  = "example"
          image = "nginx:latest"
        }
      }
    }
  }
}

resource "kubernetes_service" "example" {
  metadata {
    name = "example-service"
  }

  spec {
    selector = {
      app = "example"
    }

    port {
      port        = 80
      target_port = 80
    }

    type = "LoadBalancer"
  }
}
