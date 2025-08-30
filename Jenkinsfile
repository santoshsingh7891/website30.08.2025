pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build & Test') {
            agent {
                docker {
                    image 'maven:3.8.3-openjdk-17'
                    args '-v /root/.m2:/root/.m2' // Cache dependencies
                }
            }
            steps {
                sh 'mvn clean install'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying application...'
            }
        }
    }

    post {
        failure {
            echo 'Pipeline failed. Check the logs.'
        }
        success {
            echo 'Pipeline executed successfully.'
        }
    }
}
