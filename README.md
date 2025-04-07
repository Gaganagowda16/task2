# task-1
# Node.js Todo App – CI/CD Pipeline with Docker and GitHub Actions

This project demonstrates a complete CI/CD pipeline for a Node.js application using Docker, GitHub Actions, and DockerHub.

---

## 🚀 What’s Included

- **Node.js App**: A simple todo app built in Node.js with Mocha test cases.
- **Docker**: The app is containerized using a Dockerfile.
- **GitHub Actions**: CI/CD pipeline is configured to:
  - Install dependencies
  - Run tests 
  - Build Docker image
  - Push image to DockerHub

---

## 📁 Folder Structure

- `node-todo-cicd/`: Contains the Node.js application (`app.js`, `package.json`, tests, Dockerfile)
- `.github/workflows/main.yml`: CI/CD pipeline defined here

---

## ⚙️ CI/CD Pipeline Workflow

Whenever code is pushed to the `main` branch:

1. Code is checked out
2. Node.js and dependencies are installed
3. Tests are run using Mocha
4. Docker image is built and tagged as `sppranam06/app.js`
5. DockerHub login using secrets
6. Docker image is pushed to DockerHub

---

## 🔐 GitHub Secrets Used

Set in **Repo → Settings → Secrets and variables → Actions**:

- `DOCKERHUB_USERNAME`: Your DockerHub username
- `DOCKERHUB_TOKEN`: DockerHub access token (generated in DockerHub → Account Settings → Security)

---

## 🐳 DockerHub

Once pushed, the image can be found at:

**https://hub.docker.com/r/sppranam06/app.js**

---

## ✅ How to Test the Setup

1. Make a small change in `app.js` or test file
2. Commit and push to `main` branch
3. Go to GitHub → Actions tab → Monitor the job
4. Confirm image is updated on DockerHub

---

## 🛠️ Technologies Used

- Node.js
- Mocha (for testing)
- Docker
- GitHub Actions

---

## 👨‍💻 Developed By

**SPPranam**

Cloud Application Developer | DevOps Enthusiast
