# My Jenkins CI/CD Pipeline Project

A robust CI/CD pipeline project utilizing a declarative `Jenkinsfile` running within a containerized environment (WSL2/Docker & Jenkins).

## 🚀 Project Overview
This project demonstrates Pipeline-as-Code principles using Jenkins. The build configuration pulls code directly from GitHub via SCM, installs application dependencies, executes automated tests, builds a Docker container image, securely authenticates with Docker Hub using access tokens, pushes the image to the registry, and manages artifacts.

* **Repository:** `https://github.com/Feezcodev/my-jenkins-project`
* **Branch:** `main`
* **Orchestration Tool:** Jenkins CI

## 🧰 Tech Stack & Environment
* **Environment:** Windows Subsystem for Linux (WSL2 / Ubuntu)
* **Containerization:** Docker, Docker Compose, & Jenkins Container (with Node.js/npm installed)
* **CI/CD Server:** Jenkins (Declarative Pipeline-as-Code)
* **Version Control:** Git & GitHub
* **Container Registry:** Docker Hub (via secure Personal Access Tokens & System Global Credentials)

## ⚙️ Jenkins Setup Instructions
1. **Install Jenkins:** Run Jenkins locally or via Docker exposing port `8080`.
2. **Configure Global Credentials:** Add your Docker Hub credentials (`docker-hub-credentials`) under **Manage Jenkins > Credentials > System > Global** using a Read & Write Personal Access Token.
3. **Configure SCM:** Create a new **Pipeline** job in Jenkins.
4. **Pipeline Definition:** Select **Pipeline script from SCM**, choose **Git**, and provide your repository URL (`https://github.com/Feezcodev/my-jenkins-project`).
5. **Container Dependencies:** Ensure Node.js and npm are installed within the Jenkins container runner to handle build and test phases.

## 🔄 Pipeline Stages Architecture
* **Build:** Installs dependencies via `npm install` and generates build outputs (`build_output.txt`).
* **Test:** Executes automated validation suites (`npm test`).
* **Docker Build:** Executes `docker build -t my-jenkins-app:latest .` using the local Docker daemon socket.
* **Docker Push:** Securely logs into Docker Hub using `withCredentials` and pushes the container image.
* **Deploy / Artifact:** Archives build artifacts (`build_output.txt`) with fingerprinting enabled.

## 📊 Validation & Execution
Successfully verified and executed using Jenkins Pipeline SCM configuration with green-status build completion (Build #17), secure registry authentication, and full stage visibility.

### 📸 Pipeline Execution Screenshots
* **Successful Build Status (Green #17):**
  `![Successful Build](screenshots/build-success.png)`
* **Console Output Verification:**
  `![Console Output](screenshots/console-output.png)`
* **Docker Hub Pushed Image:**
  `![Docker Hub Pushed](screenshots/dockerhub-image-pushed.PNG)`