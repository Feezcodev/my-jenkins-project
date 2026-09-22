# My Jenkins CI/CD Pipeline Project

A robust CI/CD pipeline project utilizing a declarative `Jenkinsfile` running within a containerized environment (WSL2/Docker & Jenkins).

## 🚀 Project Overview
This project demonstrates Pipeline-as-Code principles using Jenkins. The build configuration pulls code directly from GitHub via SCM, installs application dependencies, executes automated tests, builds a Docker container image, and manages artifacts.

* **Repository:** `https://github.com/Feezcodev/my-jenkins-project`
* **Branch:** `main`
* **Orchestration Tool:** Jenkins CI

## 🧰 Tech Stack & Environment
* **Environment:** Windows Subsystem for Linux (WSL2 / Ubuntu)
* **Containerization:** Docker, Docker Compose, & Jenkins Container (with Node.js/npm installed)
* **CI/CD Server:** Jenkins (Declarative Pipeline-as-Code)
* **Version Control:** Git & GitHub

## ⚙️ Jenkins Setup Instructions
1. **Install Jenkins:** Run Jenkins locally or via Docker exposing port `8080`.
2. **Configure SCM:** Create a new **Pipeline** job in Jenkins.
3. **Pipeline Definition:** Select **Pipeline script from SCM**, choose **Git**, and provide your repository URL (`https://github.com/Feezcodev/my-jenkins-project`).
4. **Container Dependencies:** Ensure Node.js and npm are installed within the Jenkins container runner to handle build and test phases.

## 🔄 Pipeline Stages Architecture
* **Build:** Installs dependencies via `npm install` and generates build outputs (`build_output.txt`).
* **Test:** Executes automated validation suites (`npm test`).
* **Docker Build:** Executes `docker build -t my-jenkins-app:latest .` using the local Docker daemon socket.
* **Deploy / Artifact:** Archives build artifacts (`build_output.txt`) with fingerprinting enabled.

## 📊 Validation & Execution
Successfully verified and executed using Jenkins Pipeline SCM configuration with green-status build completion (Build #10), archived artifacts, and full stage visibility.

### 📸 Pipeline Execution Screenshots
* **Successful Build Status (Green #10):**
  *(Add your screenshot here: `![Successful Build](screenshots/build-success.png)`)*
* **Console Output Verification:**
  *(Add your screenshot here: `![Console Output](screenshots/console-output.png)`)*