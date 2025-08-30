pipeline {
    agent {
        docker { 
            image 'maven:3.8.3-openjdk-17'
            args '-v /root/.m2:/root/.m2' // optional: cache Maven dependencies
        }
    }

    environment {
        MAVEN_OPTS = "-Xmx1024m"
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo 'Building the project...'
                sh 'mvn clean install'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                sh 'mvn test'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying the application...'
                // Add your deployment commands here
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed. Check logs.'
        }
    }
}
