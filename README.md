# 🚀 Task 3 — Infrastructure as Code (IaC) with Terraform & Docker

## 📌 Project Overview

This project demonstrates Infrastructure as Code (IaC) using Terraform to provision a local Docker container.

Terraform is used to download the Nginx Docker image and create an Nginx container with port mapping.

## 🎯 Objective

The objective of this task is to understand how Terraform can create, manage, and destroy infrastructure using code.

## 🛠️ Technologies Used

- Terraform
- Docker
- Docker Desktop
- Nginx
- Git & GitHub

## 🔄 Infrastructure Workflow

Terraform Configuration → terraform init → terraform plan → terraform apply → Docker Nginx Container → Application Verification → terraform state → terraform destroy

## 📂 Project Structure

terraform-docker-task/
├── main.tf
├── .gitignore
├── .terraform.lock.hcl
├── Screenshot 2026-10-05 215812.png
├── Screenshot 2026-10-05 215920.png
├── Screenshot 2026-10-05 215929.png
└── README.md

## ⚙️ Terraform Configuration

The main.tf file uses the Docker provider to create an Nginx image and Docker container.

Terraform configuration:

terraform {
  required_providers {
    docker = {
      source  = "kreuzwerker/docker"
      version = "~> 3.0"
    }
  }
}

provider "docker" {}

resource "docker_image" "nginx" {
  name = "nginx:latest"
}

resource "docker_container" "nginx" {
  name  = "terraform-nginx"
  image = docker_image.nginx.image_id

  ports {
    internal = 80
    external = 8081
  }
}

## 1️⃣ Terraform Init

Command: terraform init

Terraform successfully initialized the project and installed the Docker provider.

Provider installed: kreuzwerker/docker v3.9.0

## 2️⃣ Terraform Plan

Command: terraform plan

Terraform displayed the infrastructure that would be created.

Result: Plan: 2 to add, 0 to change, 0 to destroy.

The planned resources were:

- Nginx Docker image
- Nginx Docker container

## 3️⃣ Terraform Apply

Command: terraform apply

After confirming with "yes", Terraform created the Docker container.

Result: Apply complete! Resources: 1 added, 0 changed, 0 destroyed.

The Nginx container was successfully created.

## 4️⃣ Verify the Application

The Nginx application was accessed using:

http://localhost:8081

The Nginx welcome page was displayed successfully.

Port mapping:

Host Port 8081 → Container Port 80

## 5️⃣ Check Terraform State

Command: terraform state list

Output:

docker_container.nginx
docker_image.nginx

This confirms that Terraform is tracking the Docker infrastructure using its state.

## 6️⃣ Terraform Destroy

Command: terraform destroy

After confirmation with "yes", Terraform destroys the infrastructure created by Terraform.

## 📸 Execution Evidence

The repository contains screenshots showing:

- Terraform execution
- Terraform plan
- Docker Nginx container creation
- Nginx application running on localhost:8081
- Terraform state verification

## 🔐 Terraform State Management

Terraform maintains infrastructure information using its state file.

The following files are excluded from Git using .gitignore:

.terraform/
*.tfstate
*.tfstate.*

This prevents local Terraform state and downloaded provider files from being uploaded to GitHub.

## ✅ Result

Successfully provisioned a local Nginx Docker container using Terraform.

The complete Infrastructure as Code workflow was successfully demonstrated:

Terraform Configuration → Init → Plan → Apply → Docker Container → Verification → State → Destroy

## 🎓 What I Learned

- Infrastructure as Code (IaC)
- Terraform fundamentals
- Terraform providers
- Terraform resources
- Docker provider
- terraform init
- terraform plan
- terraform apply
- terraform state
- terraform destroy
- Docker container provisioning
- Terraform state management
- Managing infrastructure using code

## 👩‍💻 Author

Kirthika

GitHub: https://github.com/kirthika25160
