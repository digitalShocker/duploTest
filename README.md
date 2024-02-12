

# Terraform EKS Deployment Guide

## Introduction
This guide is designed for software developers with no prior cloud experience. It walks you through deploying an Amazon EKS cluster and associated services/applications using Terraform, directly from AWS CloudShell.

## Prerequisites
- Latest version of Chrome on a Mac.
- Admin rights in AWS for networking and EKS deployment.

## Getting Started

### Step 1: Access AWS CloudShell
1. Log into the [AWS console](https://aws.amazon.com/console/).
2. Press `option + s` and start typing "CloudShell." Select it when it appears.
3. Once in CloudShell, you're ready to proceed. AWS CLI is pre-installed.

### Step 2: Install Terraform in CloudShell
Run the following commands to install Terraform:

```
sudo yum install -y yum-utils
sudo yum-config-manager --add-repo https://rpm.releases.hashicorp.com/AmazonLinux/hashicorp.repo
sudo yum -y install terraform
```

For a list of packages in CloudShell: [AWS CloudShell Packages](https://docs.aws.amazon.com/cloudshell/latest/userguide/vm-specs.html)

### Step 3: Clone the Project Repository
Clone the repository to get the Terraform configuration files:

```
git clone https://github.com/digitalShocker/duploTest.git
```

### Step 4: Deploy the EKS Cluster
1. Change directory to the cloned repo, specifically into the `eksCluster` directory.
2. Initialize Terraform: `terraform init`
3. Apply the Terraform configuration: `terraform apply` and confirm with `yes`.
4. After deployment, verify the cluster is up: 

```
aws eks --region $(terraform output -raw region) update-kubeconfig --name $(terraform output -raw cluster_name)
```

### Step 5: Deploy Services & Applications
1. Move to the `eksDeploy` directory: `cd ../eksDeploy`
2. Run `terraform init` and `terraform apply` again. You may need to clean up previous directories for space.
3. Once complete, an output provides the URL of the load balancer.

### Step 6: Access Your Deployment
- Copy the load balancer URL from the output and paste it into Chrome. 
- It might take about 8 minutes for the site to become accessible due to DNS propagation.

---
