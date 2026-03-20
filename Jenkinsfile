pipeline {
    agent any

    environment {
        IMAGE_NAME = "akshayaa04/devops-app:v1"
    }

    stages {

        stage('Clone Repo') {
            steps {
                git 'https://github.com/<your-username>/devops-jenkins-app.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'pip install -r requirements.txt'
            }
        }

        stage('Lint') {
            steps {
                sh 'flake8 . || true'
            }
        }

        stage('Test') {
            steps {
                sh 'pytest || true'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $IMAGE_NAME .'
            }
        }

        stage('Run Container') {
            steps {
                sh 'docker run -d -p 5002:5000 $IMAGE_NAME'
            }
        }
    }
}

