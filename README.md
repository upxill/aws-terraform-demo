# AWS S3 Bucket Provisioning with Terraform

A minimal Terraform configuration that provisions a single AWS S3 bucket using the HashiCorp AWS provider. It's a compact, self-contained reference for the core Terraform workflow (`init` → `plan` → `apply`) on AWS — a starting point rather than a production stack.

## How this differs from my other infra/DevOps repos

This is the AWS half of a two-cloud Terraform pairing. It provisions an S3 bucket with the AWS provider and local state, while [`terraform-demo`](../terraform-demo) provisions the equivalent object-storage resource on GCP (a GCS bucket) and wires up a Terraform Cloud remote backend/workspace. Together they show the same basic IaC pattern — "stand up one storage bucket" — implemented across two different clouds and two different state-management approaches.

## Tech Stack

- Terraform (>= 1.0)
- HashiCorp AWS provider (`~> 5.0`)
- AWS S3

## Architecture

The entire configuration lives in one file, `main.tf`:

- A `required_providers` block pins the AWS provider to `~> 5.0`.
- A `provider "aws"` block targets the `us-east-1` region.
- A single `aws_s3_bucket.my_bucket` resource creates a bucket (`my-terraform-cloud-s3-example`) tagged `Name = MyBucket`, `Environment = Dev`.

There's no remote backend configured, so state is local (`terraform.tfstate` in the working directory) unless you add one yourself.

## Getting Started

**Prerequisites**

- [Terraform](https://www.terraform.io/downloads.html) v1.0+
- An AWS account and credentials with permission to create S3 buckets

**Configure AWS credentials** (any one of):

```bash
aws configure
# or
export AWS_ACCESS_KEY_ID="your-access-key"
export AWS_SECRET_ACCESS_KEY="your-secret-key"
export AWS_DEFAULT_REGION="us-east-1"
```

**Run it**

```bash
terraform init
terraform plan
terraform apply
```

**Tear down**

```bash
terraform destroy
```

> Note: `main.tf` sets `acl = "private"` directly on `aws_s3_bucket`. That inline `acl` argument was removed from the AWS provider in v4+ and this config pins `~> 5.0`, so `terraform apply` will likely fail as written — see Cleanup Notes.

## Project Structure

```
aws-terraform-demo/
├── main.tf      # provider config + single S3 bucket resource
└── README.md
```
