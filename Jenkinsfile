pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'master', url: 'https://github.com/hshar/website.git'
            }
        }

        stage('Build') {
            steps {
                echo 'Building the project...'
                sh 'mvn clean install || true'   // if using Maven, else adjust
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                sh 'echo "No tests configured yet!"'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying to server...'
                // Example deploy via Ansible or copy files
                sh 'ansible-playbook -i inventory.ini deploy.yml'
            }
        }
    }

    post {
        always {
            echo 'Pipeline finished.'
        }
    }
}
