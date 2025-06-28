# 🚀 S3 Static Website Hosting with Terraform & GitHub Actions

This project demonstrates how to provision an **Amazon S3 bucket** using **Terraform** and deploy a static website to it automatically using **GitHub Actions**.

---

## 📁 Project Structure

```bash
.
├── main.tf                  # Terraform config for S3 bucket + IAM policies
├── oxer-html/               # Static site files (HTML/CSS/JS)
├── .github/workflows/
│   └── deploy.yml           # GitHub Actions workflow for Terraform deployment
└── README.md



🔧 Prerequisites
AWS account
IAM user with permissions to manage S3 & IAM
Terraform v1.12+
AWS CLI (configured locally if testing)
GitHub repository secrets:
AWS_ACCESS_KEY_ID
AWS_SECRET_ACCESS_KEY



🌐 What It Does
Creates an S3 bucket with:
Static website hosting (index.html, error.html)
Public access permissions
Versioning
Deploys contents of oxer-html/ to the bucket using GitHub Actions
Auto-deploys on main branch pushes


🚀 Deploy Instructions
1. Clone the repo
    git clone https://github.com/your-org/s3-bucket-website-hosting-terraform.git
    cd s3-bucket-website-hosting-terraform

2. Initialize and apply Terraform (optional local test)
    terraform init
    terraform plan
    terraform apply
    Or skip local runs and let GitHub Actions handle deployment.

3. Push your changes to GitHub
    git add .
    git commit -m "Deploy S3 website with Terraform"
    git push origin main
    ⚙️ GitHub Actions Workflow
    .github/workflows/deploy.yml:

Runs on every push to main
    Uses aws-actions/configure-aws-credentials to authenticate
    Applies Terraform configuration
    Uploads website content from oxer-html/ to S3 bucket
    🌍 Access Your Site
    Once deployed, visit:
    http://<your-bucket-name>.s3-website.<region>.amazonaws.com

Example:
    http://my-tf-bucket-demo-2025-test.s3-website.ap-south-1.amazonaws.com

🧹 Clean Up
    To destroy resources created by Terraform:
    terraform destroy