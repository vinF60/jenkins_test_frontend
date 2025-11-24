pipeline {
    agent any

    stages {

        stage('Clone') {
            steps {
                git 'https://github.com/vinF60/jenkins_test_frontend.git'
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
                sh "docker run -d --name frontend -p 3001:3001 frontend-app:latest"
            }
        }
    }
}
