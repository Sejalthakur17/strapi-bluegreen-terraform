## Task 10 & 11 – Blue/Green Deployment with CI/CD (ECS + CodeDeploy + GitHub Actions)

## Project Overview
This project implements a Blue/Green deployment strategy for an application running on:

AWS ECS (Fargate)

AWS CodeDeploy

Application Load Balancer (ALB)

Amazon ECR

GitHub Actions CI/CD

The goal is to:

Automatically build and push Docker images

Update ECS Task Definitions dynamically

Trigger Blue/Green deployment using CodeDeploy

Ensure zero-downtime deployments

Support rollback on failure

## Architecture
GitHub Push
    ↓
GitHub Actions
    ↓
Build Docker Image
    ↓
Push to Amazon ECR (tagged with commit SHA)
    ↓
Update ECS Task Definition
    ↓
Trigger CodeDeploy Deployment
    ↓
Blue/Green Traffic Shift via ALB

## Repository Structure
.github/workflows/
    terraform.yml
    cd.yml
    ci.yml

modules/
    vpc/
    security_groups/
    alb/
    ecs/
    rds/
    codedeploy/

main.tf
variables.tf
outputs.tf
providers.tf

## Rollback Strategy

Automatic rollback is enabled in CodeDeploy if:

Deployment fails

Health checks fail

Traffic shift fails

Rollback ensures zero downtime.

## Access application using:

http://alb_dns_name/admin
