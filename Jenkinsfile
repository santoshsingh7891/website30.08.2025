pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean install'
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Deploy') {
            when {
                branch 'master'  // Make sure this matches your production branch
            }
            steps {
                sh 'ansible-playbook -i inventory.ini deploy.yml'
            }
        }
    }
}

