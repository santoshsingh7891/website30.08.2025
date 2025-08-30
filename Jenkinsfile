pipeline {
    agent any

    stages {
        stage('Checkout SCM') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/santoshsingh7891/website30.08.2025.git',
                    credentialsId: 'YOUR_GITHUB_CREDENTIAL_ID'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean install'
            }
        }

        stage('Test') {
            steps {
                sh 'echo "No tests configured yet!"'
            }
        }

        stage('Deploy') {
            steps {
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
