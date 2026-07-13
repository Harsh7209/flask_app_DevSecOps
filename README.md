# Flask App — DevSecOps Demo

A small Flask web application adopted and enhanced to demonstrate DevSecOps practices: secure coding, automated security checks in CI/CD, container image scanning, and optional infrastructure-as-code checks and GitOps deployment.

---

## Table of Contents
- [Project Overview](#project-overview)
- [Key Features](#key-features)
- [Tech Stack](#tech-stack)
- [DevSecOps Implementations](#devsecops-implementations)
- [CI/CD Pipeline (recommended)](#cicd-pipeline-recommended)
- [Getting Started (Local)](#getting-started-local)
- [Run with Docker](#run-with-docker)
- [Running Security Scans Locally](#running-security-scans-locally)
- [Project Structure](#project-structure)
- [Contributing](#contributing)
- [License](#license)
- [Author / Contact](#author--contact)

---

## Project Overview
This repository contains a lightweight Flask web application that was adopted from an open-source project and extended to showcase practical DevSecOps techniques. The goal is to provide a concise example you can run locally, scan, and integrate into CI/CD to learn secure-by-design workflows.

This README documents the project's goals, security integrations, and how to run and scan the app locally or in CI.

---

## Key Features
- Minimal Flask application (example web app) suitable for demos and learning
- Containerized with Docker
- Example GitHub Actions CI/CD pipeline with security stages (examples provided)
- Integrations and guidance for:
  - Static application security testing (SAST)
  - Dependency vulnerability scanning
  - Container image scanning
  - Secret detection
  - (Optional) IaC security checks and GitOps deployment

---

## Tech Stack
- Backend: Python + Flask
- Containerization: Docker
- CI/CD: GitHub Actions
- Security tooling (examples): Bandit, Trivy, Gitleaks, pip-audit, OWASP ZAP, tfsec / checkov
- (Optional infra): Terraform, Kubernetes, ArgoCD, EKS
- Observability examples: Prometheus, Grafana

---

## DevSecOps Implementations
This repository demonstrates security controls across the development lifecycle:

- Secure code practices
  - Avoid hardcoded secrets
  - Basic SAST with Bandit
- CI/CD security gates
  - Example automated checks in GitHub Actions (lint → test → SAST → dependency scan → build → container scan → deploy)
- Secret scanning
  - Gitleaks for detecting secrets in history
- Container image scanning
  - Trivy to scan built images for vulnerabilities
- (Optional) Infrastructure scanning
  - tfsec / checkov for Terraform IaC checks
- GitOps (optional)
  - ArgoCD for continuous delivery of Kubernetes manifests

Notes: The repository contains placeholders for many integrations. Review and adapt the example workflows to match your environment and policies.

---

## CI/CD Pipeline (recommended)
A secure pipeline example for this project:

1. Checkout code
2. Create environment / install dependencies
3. Run tests and linters
4. Static analysis (Bandit / SAST)
5. Dependency scanning (pip-audit / safety)
6. Build Docker image
7. Scan Docker image (Trivy)
8. Secret scan (Gitleaks)
9. If all checks pass → push image & deploy, or update GitOps repo for ArgoCD

---

## Getting Started (Local)
Clone the repo and run locally.

1. Clone:

   git clone https://github.com/Harsh7209/flask_app_DevSecOps.git
   cd flask_app_DevSecOps

2. Create a virtual environment and install dependencies:

   python -m venv .venv
   source .venv/bin/activate   # Windows: .venv\Scripts\activate
   pip install -r requirements.txt

3. Run the app:

   python app.py

4. Open http://localhost:5000 in your browser.

---

## Run with Docker
Build and run the container:

1. Build:

   docker build -t flask-devsecops .

2. Run:

   docker run -p 5000:5000 flask-devsecops

Visit http://localhost:5000.

---

## Running Security Scans Locally
Install the tools locally (or run them via their Docker images) and run these example commands:

- Bandit (SAST for Python):
  pip install bandit
  bandit -r .

- Trivy (container image scan):
  # build image first, then:
  trivy image flask-devsecops:latest

- Gitleaks (secret detection in repo):
  # install gitleaks, then:
  gitleaks detect --source .

- pip-audit (dependency vulnerability scan):
  pip install pip-audit
  pip-audit

- tfsec / checkov (if Terraform present):
  tfsec .
  checkov -d .

Adjust options to integrate these into CI.

---

## Project Structure
.
├── app.py
├── requirements.txt
├── Dockerfile
├── .github/workflows/        # Example/actual pipeline YAMLs
└── templates/

(If you add Terraform, Kubernetes manifests, or Helm charts, group them into /infra, /k8s, or /charts.)

---

## Contributing
Contributions and improvements are welcome — especially for:
- Adding concrete CI workflows (GitHub Actions) used in the repo
- Including sample Terraform / Kubernetes manifests and GitOps examples
- Adding tests and code quality checks
- Improving documentation and developer setup

Please open issues or PRs on GitHub.

---

## License
This repository currently does not contain a LICENSE file. If you want to publish under a license, consider adding a LICENSE file (for example, the MIT License).

---

## Author / Contact
Harsh Choubey  
https://github.com/Harsh7209  
harshchoubey113@gmail.com

---

### Next steps I can take for you
- Add example GitHub Actions workflow files for Bandit / Trivy / Gitleaks under .github/workflows/
- Add a LICENSE file (MIT) or CONTRIBUTING.md
- Add simple Terraform / Kubernetes example structure

Tell me which you'd like and I will create and commit the files.
