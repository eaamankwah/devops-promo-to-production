# DevOps Promotion to Production 🚀

[![CircleCI](https://img.shields.io/circleci/build/github/eaamankwah/devops-promo-to-production/main?style=for-the-badge&logo=circleci)](https://circleci.com/gh/eaamankwah/devops-promo-to-production)
[![AWS](https://img.shields.io/badge/AWS-CloudFormation-FF9900?style=for-the-badge&logo=amazon-aws)](https://aws.amazon.com/cloudformation/)
[![Infrastructure](https://img.shields.io/badge/Infrastructure-as%20Code-blue?style=for-the-badge&logo=terraform)](https://www.terraform.io/)

> **A comprehensive DevOps solution demonstrating automated CI/CD pipeline implementation with AWS infrastructure provisioning and CloudFront distribution management.**

## 📋 Table of Contents

* [Overview](#overview)
* [Architecture](#architecture)
* [Features](#features)
* [Prerequisites](#prerequisites)
* [Project Structure](#project-structure)
* [Getting Started](#getting-started)
* [Deployment Pipeline](#deployment-pipeline)
* [Infrastructure Components](#infrastructure-components)
* [Configuration](#configuration)
* [Monitoring & Logging](#monitoring--logging)
* [Troubleshooting](#troubleshooting)
* [Contributing](#contributing)

## 🎯 Overview

This project showcases a production-ready DevOps implementation featuring automated deployment pipelines, infrastructure as code, and cloud-native architecture patterns. The solution demonstrates best practices in continuous integration, continuous deployment, and infrastructure management using modern DevOps tools and AWS services.

### Key Objectives
* **Automation**: Fully automated deployment pipeline from code commit to production
* **Scalability**: Cloud-native architecture supporting horizontal scaling
* **Reliability**: Infrastructure as code ensuring consistent deployments
* **Security**: Best practices implementation for secure cloud deployments

## 🏗️ Architecture

```
┌─────────────────┐    ┌──────────────────┐    ┌─────────────────┐
│   Developer     │    │    CircleCI      │    │   AWS Cloud     │
│   Workstation   │───▶│   CI/CD Pipeline │───▶│  Infrastructure │
└─────────────────┘    └──────────────────┘    └─────────────────┘
                                │                        │
                                ▼                        ▼
                       ┌──────────────────┐    ┌─────────────────┐
                       │  Build & Test    │    │   S3 Bucket     │
                       │   Automation     │    │  + CloudFront   │
                       └──────────────────┘    └─────────────────┘
```

## ✨ Features

### 🔄 **Continuous Integration/Continuous Deployment**
* Automated build and deployment pipeline using CircleCI
* Multi-stage deployment process with quality gates
* Automated testing integration
* Rolling deployment strategies

### ☁️ **Cloud Infrastructure**
* **Amazon S3**: Static website hosting and artifact storage
* **CloudFront CDN**: Global content delivery with edge caching
* **Infrastructure as Code**: CloudFormation templates for reproducible deployments

### 🛡️ **Security & Best Practices**
* Secure credential management
* Infrastructure compliance validation
* Automated security scanning integration
* Access control and permission management

### 📊 **Monitoring & Observability**
* Deployment status tracking
* Infrastructure health monitoring
* Performance metrics collection
* Automated alerting systems

## 🔧 Prerequisites

Before getting started, ensure you have the following tools and accounts configured:

### Required Tools
```bash
# AWS CLI
aws --version
# Should return: aws-cli/2.x.x Python/3.x.x

# Git
git --version
# Should return: git version 2.x.x

# Node.js (if applicable)
node --version
npm --version
```

### Required Accounts & Permissions
* **AWS Account** with appropriate IAM permissions
* **CircleCI Account** connected to your GitHub repository
* **GitHub Repository** with proper webhook configuration

### AWS IAM Permissions
Your AWS user/role needs the following permissions:
* S3 bucket creation and management
* CloudFront distribution management
* CloudFormation stack operations
* IAM role creation (for service roles)

## 📁 Project Structure

```
devops-promo-to-production/
├── .circleci/
│   └── config.yml              # CircleCI pipeline configuration
├── infrastructure/
│   ├── bucket.yml              # S3 bucket CloudFormation template
│   └── cloudfront.yml          # CloudFront distribution template
├── src/
│   └── index.html              # Application source code
├── scripts/
│   ├── deploy.sh               # Deployment automation scripts
│   └── validate.sh             # Infrastructure validation
├── docs/
│   └── DEPLOYMENT.md           # Detailed deployment guide
└── README.md                   # Project documentation
```

## 🚀 Getting Started

### 1. Clone the Repository
```bash
git clone https://github.com/eaamankwah/devops-promo-to-production.git
cd devops-promo-to-production
```

### 2. Configure AWS Credentials
```bash
# Configure AWS CLI
aws configure

# Verify configuration
aws sts get-caller-identity
```

### 3. Set Up CircleCI Environment Variables
Navigate to your CircleCI project settings and configure:

| Variable Name | Description | Example |
|---------------|-------------|---------|
| `AWS_ACCESS_KEY_ID` | AWS access key | `AKIAIOSFODNN7EXAMPLE` |
| `AWS_SECRET_ACCESS_KEY` | AWS secret key | `wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY` |
| `AWS_DEFAULT_REGION` | AWS region | `us-east-1` |
| `S3_BUCKET_NAME` | S3 bucket name | `my-app-production-bucket` |

### 4. Deploy Infrastructure
```bash
# Deploy S3 bucket
aws cloudformation deploy \
  --template-file bucket.yml \
  --stack-name production-bucket \
  --capabilities CAPABILITY_IAM

# Deploy CloudFront distribution
aws cloudformation deploy \
  --template-file cloudfront.yml \
  --stack-name production-cloudfront \
  --capabilities CAPABILITY_IAM
```

## 🔄 Deployment Pipeline

The CI/CD pipeline follows these stages:

### Stage 1: Code Quality & Testing
```yaml
 checkout: Source code retrieval
 install: Dependency installation
 lint: Code quality checks
 test: Unit and integration tests
 security-scan: Security vulnerability assessment
```

### Stage 2: Build & Package
```yaml
 build: Application compilation
 package: Artifact creation
 docker-build: Container image creation (if applicable)
 artifact-upload: Build artifact storage
```

### Stage 3: Infrastructure Validation
```yaml
 infrastructure-lint: CloudFormation template validation
 security-check: Infrastructure security compliance
 cost-estimation: Deployment cost analysis
```

### Stage 4: Deployment
```yaml
 staging-deploy: Staging environment deployment
 integration-tests: End-to-end testing
 production-deploy: Production deployment
 smoke-tests: Post-deployment validation
```

## 🏛️ Infrastructure Components

### Amazon S3 Configuration
```yaml
# Key S3 bucket features
 Static Website Hosting: Enabled
 Versioning: Enabled for rollback capability
 Encryption: AES-256 server-side encryption
 Access Logging: Enabled for audit trails
 Lifecycle Policies: Automated cleanup of old versions
```

### CloudFront Distribution
```yaml
# CDN configuration highlights
 Global Edge Locations: Worldwide content delivery
 Custom Domain: Support for custom SSL certificates
 Caching Policies: Optimized for static content
 Security Headers: HTTPS redirect and security headers
 Origin Access Identity: Secure S3 bucket access
```

## ⚙️ Configuration

### Environment-Specific Settings

#### Development
```bash
export ENVIRONMENT=development
export S3_BUCKET=dev-bucket-name
export CLOUDFRONT_DISTRIBUTION=DEV123456789
```

#### Staging
```bash
export ENVIRONMENT=staging
export S3_BUCKET=staging-bucket-name
export CLOUDFRONT_DISTRIBUTION=STG123456789
```

#### Production
```bash
export ENVIRONMENT=production
export S3_BUCKET=prod-bucket-name
export CLOUDFRONT_DISTRIBUTION=PRD123456789
```

### CircleCI Configuration Highlights

```yaml
# Key pipeline features
workflows:
  - parallel_execution: Multiple jobs run simultaneously
  - conditional_deployment: Environment-based deployments
  - approval_gates: Manual approval for production
  - rollback_capability: Automated rollback on failure
```

## 📊 Monitoring & Logging

### AWS CloudWatch Integration
* **Application Metrics**: Response times, error rates, throughput
* **Infrastructure Metrics**: CPU utilization, memory usage, network I/O
* **Custom Dashboards**: Real-time operational visibility
* **Automated Alerts**: Proactive issue notification

### Logging Strategy
```bash
# Application logs
/var/log/application/app.log

# Deployment logs
/var/log/deployment/deploy.log

# Infrastructure logs
CloudWatch Logs Groups:
 /aws/s3/access-logs
 /aws/cloudfront/access-logs
```

## 🔍 Troubleshooting

### Common Issues & Solutions

#### Pipeline Failures
```bash
# Check CircleCI build logs
circleci-cli logs <build-number>

# Validate CloudFormation templates
aws cloudformation validate-template --template-body file://bucket.yml
```

#### S3 Deployment Issues
```bash
# Verify bucket permissions
aws s3api get-bucket-policy --bucket <bucket-name>

# Check bucket website configuration
aws s3api get-bucket-website --bucket <bucket-name>
```

#### CloudFront Issues
```bash
# Check distribution status
aws cloudfront get-distribution --id <distribution-id>

# Invalidate cache
aws cloudfront create-invalidation --distribution-id <id> --paths "/*"
```

### Performance Optimization
* **Caching Strategy**: Implement appropriate cache headers
* **Image Optimization**: Compress and optimize static assets
* **CDN Configuration**: Fine-tune CloudFront cache behaviors
* **Monitoring**: Set up performance monitoring and alerting

## 🤝 Contributing

We welcome contributions! Please follow these guidelines:

1. **Fork** the repository
2. **Create** a feature branch: `git checkout -b feature/amazing-feature`
3. **Commit** your changes: `git commit -m 'Add amazing feature'`
4. **Push** to the branch: `git push origin feature/amazing-feature`
5. **Open** a Pull Request

### Development Workflow
```bash
# Set up development environment
make setup-dev

# Run local tests
make test

# Validate infrastructure changes
make validate-infrastructure

# Submit changes
make submit-pr
```

## 📈 Project Metrics

| Metric | Value |
|--------|-------|
| Deployment Frequency | Multiple times per day |
| Lead Time for Changes | < 1 hour |
| Mean Time to Recovery | < 15 minutes |
| Change Failure Rate | < 5% |

## 📞 Support & Contact

* **Documentation**: [Project Wiki](https://github.com/eaamankwah/devops-promo-to-production/wiki)
* **Issues**: [GitHub Issues](https://github.com/eaamankwah/devops-promo-to-production/issues)
* **Discussions**: [GitHub Discussions](https://github.com/eaamankwah/devops-promo-to-production/discussions)

---

## 🏆 Technical Achievements

This project demonstrates proficiency in:

### DevOps Practices

 ✅ Infrastructure as Code (IaC)
 
 ✅ Continuous Integration/Continuous Deployment
 
 ✅ Automated Testing & Quality Gates
 
 ✅ Configuration Management
 
 ✅ Monitoring & Observability

### Cloud Technologies
 ✅ AWS Services Integration
 
 ✅ Serverless Architecture Patterns
 
 ✅ Content Delivery Networks
 
 ✅ Cloud Security Best Practices
 
 ✅ Cost Optimization Strategies

### Automation & Tooling
 ✅ Pipeline Automation with CircleCI
 
 ✅ Infrastructure Provisioning
 
 ✅ Deployment Automation
 
 ✅ Testing Automation
 
 ✅ Monitoring Automation

---

**Built with ❤️ by [Edward Amankwah](https://github.com/eaamankwah)**

*Last updated: July 2025*
