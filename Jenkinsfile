pipeline {
    agent any

    stages {

        stage('Clone') {
            steps {
                git 'https://github.com/YOUR_USER/frontend-repo.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    dockerImage = docker.build("frontend-app:latest")
                }
            }
        }

        stage('Run Container') {
            steps {
                sh "docker rm -f frontend || true"
                sh "docker run -d --name frontend -p 3000:3000 frontend-app:latest"
            }
        }
    }
}
