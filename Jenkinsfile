pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Installing dependencies...'
                sh 'npm install'
                echo 'Building application artifacts...'
                sh 'echo "App built successfully" > build_output.txt'
            }
        }
        stage('Test') {
            steps {
                echo 'Running automated tests...'
                sh 'npm test'
            }
        }
        stage('Docker Build') {
            steps {
                echo 'Building Docker image...'
                sh 'docker build -t my-jenkins-app:latest .'
            }
        }
        stage('Deploy / Artifact') {
            steps {
                echo 'Archiving build artifacts and verifying deployment simulation...'
                archiveArtifacts artifacts: 'build_output.txt', fingerprint: true
            }
        }
    }
}