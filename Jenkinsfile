pipeline {
    agent any
    stages {
        stage('Clone Code') {
            steps {
                git url: 'https://github.com/saisamala/testing-apps', branch: 'main'
            }
        }
        stage('Build') {
            steps {
                sh 'cd test-app-node-js && npm install'
            }
        }
        stage('Test') {
            steps {
                sh 'npm test'
            }
        }
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t test-app .'
            }
        }
        stage('Deploy Docker Container') {
            steps {
                sh 'docker run -d -p 3000:3000 test-app'
            }
        }
    }
}
