pipeline {
    agent any

    tools {
        maven 'Maven3'  // Make sure you have a Maven installation configured in Jenkins
        jdk 'JDK11'     // Your JDK installation
    }

    stages {
        stage('Checkout SCM') {
            steps {
                echo "Checking out source code..."
                git(
                    url: 'https://github.com/santoshsingh7891/website30.08.2025.git',
                    credentialsId: 'bc38ac40-67d6-4424-bc04-7663bbd86552'
                )
            }
        }

        stage('Build') {
            steps {
                echo "Building the project with Maven..."
                // Change directory if pom.xml is inside a subfolder (replace 'project' with actual folder)
                dir('.') {
                    sh 'mvn clean install'
                }
            }
        }

        stage('Test') {
            steps {
                echo "Running tests..."
                sh 'mvn test'
            }
        }

        stage('Deploy') {
            steps {
                echo "Deploying the project..."
                // Example: ansible-playbook or any deployment script
                sh 'ansible-playbook -i inventory.ini deploy.yml'
            }
        }
    }

    post {
        always {
            echo "Cleaning up workspace..."
            cleanWs()
        }
        success {
            echo "Pipeline completed successfully!"
        }
        failure {
            echo "Pipeline failed. Check the logs."
        }
    }
}

