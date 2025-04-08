# Task-2: Jenkins CI/CD Pipeline for Node.js App Deployment

## 📌 Objective

Automate the process of building, testing, and deploying a Node.js application using Jenkins and Docker.

---

## 🔧 Tools & Technologies Used

- Jenkins (on EC2)
- Docker & Docker Compose
- GitHub Webhooks
- GitHub Repository: [task-2](https://github.com/SPPranam/task-2)
- Node.js application (`node-todo-cicd` folder)

---

## ⚙️ Jenkins Pipeline Overview

A `Jenkinsfile` was created to define the CI/CD pipeline with the following stages:

1. **Clone Code**  
   Clones the code from GitHub repository to Jenkins workspace.

2. **Build & Test**  
   - Builds the Docker image from the `node-todo-cicd` folder.
   - Runs test script `test.js` (if present).

3. **Push to Docker Hub**  
   - Logs into Docker Hub using Jenkins credentials (`dockerHubCreds`).
   - Tags and pushes the image as `sppranam/node-app:latest`.

4. **Deploy App**  
   - Uses Docker Compose to deploy the application.

5. **Post**  
   - Prints success message after every build.

---

## 🛠 Jenkins Configuration

- Installed Jenkins on EC2 instance: [http://3.111.34.54:8080](http://3.111.34.54:8080)
- Configured a Jenkins freestyle job or pipeline job.
- Installed required plugins:
  - Git
  - Docker Pipeline
  - GitHub Integration

---

## 🔐 Credentials

- Created **Docker Hub credentials** in Jenkins under:
  - **Manage Jenkins → Credentials → dockerHubCreds**

---

## 🔁 GitHub Webhook Setup

1. Went to **GitHub Repo → Settings → Webhooks**.
2. Added a new webhook:
   - **Payload URL:** `http://3.111.34.54:8080/github-webhook/`
   - **Content type:** `application/json`
   - Enabled **push events**.

3. Enabled webhook trigger in Jenkins:
   - **Build Triggers → GitHub hook trigger for GITScm polling**

---

## 🚀 How to Trigger Pipeline

1. Make any code change, e.g., update `README.md`
2. Commit and push:
   ```bash
   git add .
   git commit -m "Trigger Jenkins pipeline"
   git push origin main

