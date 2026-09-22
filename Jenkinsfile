cat << 'EOF' > Jenkinsfile
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
        stage('Docker Push') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'docker-hub-credentials', 
                                                  usernameVariable: 'DOCKER_USER', 
                                                  passwordVariable: 'DOCKER_PASS')]) {
                    sh '''
                        echo "$DOCKER_PASS" | docker login -u "$DOCKER_USER" --password-stdin
                        docker tag my-jenkins-app:latest $DOCKER_USER/my-jenkins-app:latest
                        docker push $DOCKER_USER/my-jenkins-app:latest
                    '''
                }
            }
        }
        stage('Deploy / Artifact') {
            steps {
                echo 'Archiving build artifacts and verifying deployment simulation...'
                archiveArtifacts artifacts: 'build_output.txt', fingerprint: true
            }
        }
    }
    post {
        success {
            echo 'Pipeline executed successfully!'
        }
        failure {
            echo 'Pipeline failed! Check the console output for details.'
        }
        always {
            echo 'Pipeline run completed.'
        }
    }
}
EOF