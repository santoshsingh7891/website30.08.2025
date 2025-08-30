pipeline {
    agent any

    tools {
        // Name must match what you configured in Jenkins Global Tool Configuration
        maven 'Maven3'
    }

    environment {
        // Example: specify GitHub credentials ID
        GIT_CREDENTIALS = 'bc38ac40-67d6-4424-bc04-7663bbd86552'
    }

    stages {
        stage('Checkout SCM') {
            steps {
                echo "Checking out source code..."
                git branch: 'main',
                    url: 'https://github.com/santoshsingh7891/website30.08.2025.git',
                    credentialsId: "${GIT_CREDENTIALS}"
            }
        }

        stage('Build') {
            steps {
                echo "Building the project with Maven..."
                sh 'mvn clean install'
            }
        }

        stage('Test') {
            steps {
                echo "Running tests..."
                // Replace with actual test commands if you have any
                sh 'echo "No tests configured yet!"'
            }
        }

        stage('Deploy') {
            steps {
                echo "Deploying to server via Ansible..."
                // Make sure deploy.yml exists in your repo and inventory.ini points to correct hosts
                sh 'ansible-playbook -i inventory.ini deploy.yml'
            }
        }
    }

    post {
        success {
            echo "Pipeline completed successfully!"
        }
        failure {
            echo "Pipeline failed. Check the logs."
        }
        always {
            echo "Cleaning up workspace..."
            cleanWs()
        }
    }
}
