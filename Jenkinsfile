pipeline {
    agent { label 'maven-agent' } // Node with Maven & JDK installed
    stages {
        stage('Checkout') {
            steps { checkout scm }
        }
        stage('Build & Test') {
            steps { sh 'mvn clean install' }
        }
        stage('Deploy') {
            steps { echo 'Deploy stage placeholder' }
        }
    }
}
