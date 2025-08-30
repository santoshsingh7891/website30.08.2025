pipeline {
    agent {
        docker { image 'maven:3.8.3-openjdk-17' }
    }
    stages {
        stage('Build & Test') {
            steps {
                sh 'mvn clean install'
                sh 'mvn test'
            }
        }
        stage('Deploy') {
            when { branch 'master' }
            steps {
                sh 'ansible-playbook -i inventory.ini deploy.yml'
            }
        }
    }
}

