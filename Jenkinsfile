pipeline {
    agent any

    environment {
        IMAGE_NAME = 'gaganat16/node-app'
    }

    stages {
        stage("Clone Code") {
            steps {
                echo "Cloning your repo..."
                git url: 'https://github.com/Gaganagowda16/task2.git', branch: 'main'
            }
        }

        stage("Build & Test") {
            steps {
                echo "Building Docker image..."
                sh 'cd node-todo-cicd && docker build -t node-app .'

                echo "Running tests..."
                sh 'cd node-todo-cicd && node test.js || echo "No tests or test failed, continuing..."'
            }
        }

        stage("Push to Docker Hub") {
            steps {
                withCredentials([usernamePassword(
                    credentialsId: 'dockerHubCreds',
                    usernameVariable: 'DOCKERHUB_USER',
                    passwordVariable: 'DOCKERHUB_PASS'
                )]) {
                    sh 'echo $DOCKERHUB_PASS | docker login -u $DOCKERHUB_USER --password-stdin'
                    sh 'docker tag node-app:latest $DOCKERHUB_USER/node-app:latest'
                    sh 'docker push $DOCKERHUB_USER/node-app:latest'
                }
            }
        }

        stage("Deploy App") {
            steps {
                echo "Deploying with Docker Compose..."
                sh 'cd node-todo-cicd && docker compose down || true'
                sh 'cd node-todo-cicd && docker compose up -d --build'
            }
        }
    }
}

