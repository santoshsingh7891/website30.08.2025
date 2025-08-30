 pipeline {
    agent any

    environment {
        // Optional: set environment variables if needed
        MAVEN_OPTS = '-Xmx1024m'
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build & Test') {
            steps {
                script {
                    // Runs Maven inside the Docker container
                    docker.image('maven:3.8.3-openjdk-17').inside {
                        sh 'mvn clean install'
                    }
                }
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploy stage placeholder'
                // Add deployment commands here
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed. Check the logs.'
        }
    }
}

