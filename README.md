# AWS Terraform Demo

A simple Terraform configuration demonstrating AWS infrastructure provisioning, specifically creating an S3 bucket.

## 📋 Overview

This project provides a basic Terraform configuration to deploy AWS resources. It currently provisions an Amazon S3 bucket with proper tagging and configuration.

## 🏗️ Resources

The configuration creates the following AWS resources:

- **S3 Bucket** (`aws_s3_bucket.my_bucket`)
  - Bucket name: `my-terraform-cloud-s3-example`
  - Environment: Development
  - Tags for resource organization and cost tracking

## 📋 Prerequisites

Before you begin, ensure you have the following installed:

- [Terraform](https://www.terraform.io/downloads.html) (v1.0+)
- [AWS CLI](https://aws.amazon.com/cli/) (optional but recommended)
- AWS account with appropriate IAM permissions
- AWS credentials configured locally

### AWS Credentials Setup

Configure your AWS credentials using one of these methods:

1. **AWS CLI Configuration** (recommended):
   ```bash
   aws configure
   ```
   This will prompt you to enter your AWS Access Key ID and Secret Access Key.

2. **Environment Variables**:
   ```bash
   export AWS_ACCESS_KEY_ID="your-access-key"
   export AWS_SECRET_ACCESS_KEY="your-secret-key"
   export AWS_DEFAULT_REGION="us-east-1"
   ```

3. **AWS Credentials File**:
   - Location: `~/.aws/credentials` (Linux/Mac) or `%USERPROFILE%\.aws\credentials` (Windows)

## 🚀 Getting Started

### 1. Initialize Terraform

Initialize your Terraform working directory:

```bash
terraform init
```

This downloads the necessary provider plugins and prepares your workspace.

### 2. Review the Plan

Preview the resources that will be created:

```bash
terraform plan
```

### 3. Apply Configuration

Apply the Terraform configuration to create resources in AWS:

```bash
terraform apply
```

Review the proposed changes and type `yes` to confirm.

### 4. Verify Resources

Check your AWS console or use the AWS CLI to verify the S3 bucket was created:

```bash
aws s3 ls
```

## 🔄 Terraform Commands

Common Terraform commands for this project:

| Command | Description |
|---------|-------------|
| `terraform init` | Initialize working directory |
| `terraform plan` | Show changes required by configuration |
| `terraform apply` | Apply changes to real infrastructure |
| `terraform destroy` | Remove all remote objects managed by this configuration |
| `terraform validate` | Validate the configuration files |
| `terraform fmt` | Reformat configuration files to canonical format |
| `terraform state list` | List all resources in the state file |

## 🗑️ Cleanup

To remove all resources created by this configuration:

```bash
terraform destroy
```

Type `yes` when prompted to confirm the destruction.

## 📝 Configuration Details

### Provider Configuration
- **Provider**: AWS
- **Region**: `us-east-1`
- **Version**: `~> 5.0` (Terraform AWS Provider v5.x)

### S3 Bucket Tags
- `Name`: MyBucket
- `Environment`: Dev

## 🔐 Security Notes

- Never commit AWS credentials or sensitive data to version control
- Consider using AWS SSO for authentication in production
- Use IAM roles and policies for least-privilege access
- Regularly rotate access keys
- Enable S3 bucket versioning and encryption for production use
- Consider using Terraform Cloud for remote state management

## 📚 Additional Resources

- [Terraform AWS Provider Documentation](https://registry.terraform.io/providers/hashicorp/aws/latest/docs)
- [Terraform Best Practices](https://www.terraform.io/docs/cloud/guides/recommended-practices/index.html)
- [AWS S3 Documentation](https://docs.aws.amazon.com/s3/)
- [Terraform State Management](https://www.terraform.io/docs/language/state/)

## 🤝 Contributing

Feel free to submit issues and enhancement requests!

## 📄 License

This project is provided as-is for educational and demonstration purposes.
