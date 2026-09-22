# My Jenkins CI/CD Pipeline Project

A robust CI/CD pipeline project utilizing a declarative `Jenkinsfile` running within a containerized environment (WSL2/Docker & Jenkins).

## 🚀 Project Overview
This project demonstrates Pipeline-as-Code principles using Jenkins. The build configuration pulls code directly from GitHub via SCM, builds an application artifact, executes test verification, builds a Docker container image, and manages artifacts.

* **Repository:** `https://github.com/Feezcodev/my-jenkins-project`
* **Branch:** `main`
* **Orchestration Tool:** Jenkins CI

## 🧰 Tech Stack & Environment
* **Environment:** Windows Subsystem for Linux (WSL2 / Ubuntu)
* **Containerization:** Docker & Docker Compose, Dockerfile (`nginx:alpine` based)
* **CI/CD Server:** Jenkins (Pipeline-as-Code)
* **Version Control:** Git & GitHub

## ⚙️ Jenkins Setup Instructions
1. **Install Jenkins:** Run Jenkins locally or via Docker exposing port `8080`.
2. **Configure SCM:** Create a new **Pipeline** job in Jenkins.
3. **Pipeline Definition:** Select **Pipeline script from SCM**, choose **Git**, and provide your repository URL (`https://github.com/Feezcodev/my-jenkins-project`).
4. **Credentials:** Configure any required GitHub or Docker registry credentials under **Manage Jenkins > Credentials**.

## 🔄 Pipeline Triggers & Architecture
* **Manual Trigger:** Initiated via the Jenkins dashboard (`Build Now`).
* **Automatic Triggers (SCM Polling / Webhooks):** Configured to poll or receive push webhooks from GitHub to trigger automated runs on every commit.
* **Pipeline Stages:**
  * **Build:** Compiles or generates project build outputs (`build_output.txt`).
  * **Test:** Verifies the generated build files.
  * **Docker Build:** Executes `docker build` using the repository's `Dockerfile`.
  * **Deploy / Artifact:** Archives build artifacts and simulates deployment steps.

## 📊 Validation & Execution
Successfully verified and executed using Jenkins Pipeline SCM configuration with green-status build completion, archived artifacts, and full stage visibility.