# 🔐 Secure CI/CD Pipeline (DevSecOps)

##  Overview

This project demonstrates a **secure CI/CD pipeline** that integrates vulnerability scanning into the build process and enforces security by **failing builds when critical issues are detected**.

The goal is to simulate a real-world DevSecOps workflow where insecure code is blocked before deployment.

---

## 🚀 Key Features

* Dockerized Python (Flask) application
* CI/CD pipeline using GitHub Actions
* Container vulnerability scanning with Trivy
* Automatic pipeline failure on HIGH/CRITICAL vulnerabilities
* Clean and reproducible project structure

---

## Architecture

```
Developer → GitHub → CI Pipeline → Docker Build → Trivy Scan → Fail/Pass
```

---

## Pipeline Workflow

1. Code is pushed to the repository
2. GitHub Actions pipeline is triggered
3. Docker image is built
4. Trivy scans the image for vulnerabilities
5. Pipeline **fails if HIGH or CRITICAL vulnerabilities are detected**

---

## Security Enforcement

The pipeline is configured with:

* `exit-code: 1` → Fail on vulnerabilities
* `severity: CRITICAL,HIGH` → Focus on impactful risks
* `ignore-unfixed: true` → Avoid noise from unpatchable issues

### Example Findings

* CVE-2026-23949 (HIGH)
* CVE-2026-24049 (HIGH)

This ensures that **insecure images cannot pass the pipeline**.

---

## Run Locally

```bash
docker build -t secure-ci-app .
docker run -p 5000:5000 secure-ci-app
```

Access:
http://localhost:5000

---

## Project Structure

```
.
├── app/
│   └── app.py
├── .github/workflows/
│   └── pipeline.yml
├── Dockerfile
├── requirements.txt
├── screenshots/
└── README.md
```

---

## Screenshots

See `/screenshots` for:

* Project structure
* Application running locally
* Pipeline execution (failure)
* Trivy vulnerability scan results

---

## Skills Demonstrated

* CI/CD pipeline design
* DevSecOps security integration
* Containerisation (Docker)
* Vulnerability management
* GitHub Actions automation

---

## Why This Project Matters

Most pipelines **build and deploy**.

This pipeline:

* **detects vulnerabilities**
* **enforces security policies**
* **blocks insecure builds**

This reflects real-world DevSecOps practices used in production environments.

---

## Future Improvements

* Push images to AWS ECR
* Deploy to ECS with CI/CD
* Integrate Infrastructure as Code (Terraform)
* Add secrets scanning (TruffleHog / Gitleaks)

---

## Security Notes

* No secrets or credentials stored in repository
* Local development only
* Security enforced at build stage (shift-left security)
