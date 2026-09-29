# Juice Shop DevSecOps Pipeline Project

This repository is used for our IE3142 DevOps Security group assignment.

The project is based on OWASP Juice Shop and focuses on:

- Containerisation using Docker and Docker Compose
- Architecture analysis and threat modelling
- Vulnerability exploit-and-fix demonstrations
- Static application security testing
- Dependency scanning
- Secrets scanning
- Container image scanning
- CI/CD security automation

## Project Baseline

The project is based on OWASP Juice Shop.

The original vulnerable baseline is preserved using the Git tag:

`baseline-unmodified`

## Prerequisites

Install the following before running the project:

- Git
- Docker Desktop
- Docker Compose

Verify Docker:

```bash
docker --version
docker compose version

## Contribution/ branching 

master = stable
develop = integration
feature/* = new work
fix/* = vulnerability fixes

## folder structure

docs/
  architecture/
  threat-model/
  risk-assessment/

evidence/
  vulnerabilities/
  sast/
  cicd/
  trivy/
  secrets/