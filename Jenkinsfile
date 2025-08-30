pipeline {
    agent any

    environment {
        DOCKER_IMAGE = 'maven:3.8.3-openjdk-17'
    }

    stages {
        stage('Checkout') {
            steps {
                echo 'Checking out code...'
                checkout scm
            }
        }

        stage('Build & Test') {
            steps {
                script {
                    echo "Running build & test inside Docker container: ${DOCKER_IMAGE}"
                    docker.image(DOCKER_IMAGE).inside('-v $WORKSPACE:/app') {
                        sh '''
                            cd /app
                            mvn clean install
                        '''
                    }
                }
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploy stage (optional)'
                // Add your deployment commands here
            }
        }
    }

    post {
        always {
            echo 'Pipeline finished.'
        }
        failure {
            echo 'Pipeline failed. Check logs.'
        }
        success {
            echo 'Pipeline succeeded!'
        }
    }
}
