pipeline {
    agent {
        docker {
            image 'maven:3.9.2-jdk-17'  // correct image tag
            args '-v /root/.m2:/root/.m2'  // optional: cache Maven repo
        }
    }

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
                branch 'master'
            }
            steps {
                sh 'ansible-playbook -i inventory.ini deploy.yml'
            }
        }
    }
}
