# Netflix Movie Deployment — DevOps Project

## Project Overview

This project demonstrates the end-to-end deployment of a containerized full-stack movie streaming application using modern DevOps practices and AWS cloud infrastructure.

The application consists of a React frontend, a Spring Boot backend, and MongoDB Atlas as the cloud database.

The deployment workflow uses GitHub Actions for CI/CD, Amazon ECR for container image storage, Docker for containerization and runtime, and Amazon EC2 as the application host.

## Architecture

```text
Developer
   │
   ▼
GitHub
   │
   ▼
GitHub Actions
   │
   ├── Build Docker Image
   │
   └── Push Image
          │
          ▼
      Amazon ECR
          │
          ▼
      Amazon EC2
          │
          ├── Docker
          │
          ├── Frontend Container
          │
          └── Backend Container
                  │
                  ▼
             MongoDB Atlas

## Technology Stack

- **Frontend:** React / Node.js
- **Backend:** Spring Boot / Java 17
- **Database:** MongoDB Atlas
- **Containerization:** Docker
- **CI/CD:** GitHub Actions
- **Container Registry:** Amazon ECR
- **Cloud Compute:** Amazon EC2
- **Cloud Provider:** AWS
- **Operating System:** Ubuntu Linux
- **Version Control:** Git / GitHub

AWS Infrastructure
Amazon EC2
Amazon Elastic Container Registry (ECR)
AWS Identity and Access Management (IAM)
Amazon VPC
Security Groups
MongoDB Atlas


CI/CD Pipeline
The application uses GitHub Actions to automate container image delivery.

FRONTEND
GitHub
   ↓
GitHub Actions
   ↓
Docker Build
   ↓
Amazon ECR

BACKEND
GitHub
   ↓
GitHub Actions
   ↓
Docker Build
   ↓
Amazon ECR

The images are subsequently pulled from Amazon ECR and deployed as Docker containers on the EC2 instance.


DEPLOYMENT
The production-style deployment runs on an Ubuntu EC2 instance using Docker.
FRONTEND
EC2 Port 3000 → Frontend Container
BACKEND
EC2 Port 8080 → Spring Boot Backend Container
DATABASE
Spring Boot Backend → MongoDB Atlas


SECURITY PRACTICES
Sensitive credentials were deliberately excluded from source control.

Examples include:

MongoDB credentials
AWS access credentials
GitHub authentication tokens

AWS credentials used by GitHub Actions are stored as GitHub repository secrets rather than hard-coded into workflow files.

MongoDB credentials are stored separately from the application source code.

TROUBLESHOOTING AND LESSONS LEARNED 
During deployment, several real-world CI/CD and containerization issues were encountered and resolved.

ECR AUTHENTICATION
The initial Docker push failed because the workflow contained an inconsistent/hard-coded ECR registry reference.
The workflow was corrected to use the registry returned by the Amazon ECR login action.

DOCKER IMAGE NAMING
A Docker push initially referenced an image tag that did not match the image created during the build.
The workflow was corrected so that the image built and the image pushed use the same repository and run-number tag.

ECR REPOSITORY CONFIGURATION
The backend pipeline initially referenced an ECR repository that did not exist in the AWS account.
The required netflix_backend ECR repository was created and the pipeline was successfully rerun.

MONGODB CONNECTIVITY
The backend was configured to use MongoDB Atlas rather than a local MongoDB installation.
The MongoDB connection URI and database configuration are supplied to the backend container through environment variables.

FINAL RESULT
The application was successfully deployed as Docker containers on an AWS EC2 instance.
The live application can be accessed through the EC2 public address.

KEY DEVOPS CONCEPT DEMONSTRATED
Git repository management
GitHub Actions CI/CD
Docker image creation
Amazon ECR
Amazon EC2
IAM roles and permissions
AWS networking
Environment variables and secrets management
MongoDB Atlas integration
Linux server administration
Container troubleshooting
Cloud deployment

Author
IfediliCloud2026

DevOps Engineering Portfolio Project
