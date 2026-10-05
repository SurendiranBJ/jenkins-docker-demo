pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                echo 'Checking out code from GitHub...'
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t jenkins-docker-demo .'
            }
        }

        stage('Run Docker Container') {
            steps {
                bat 'docker rm -f jenkins-demo || exit /b 0'
                bat 'docker run -d -p 8081:80 --name jenkins-demo jenkins-docker-demo'
            }
        }

        stage('Success') {
            steps {
                echo 'Application deployed successfully!'
            }
        }
    }
}
