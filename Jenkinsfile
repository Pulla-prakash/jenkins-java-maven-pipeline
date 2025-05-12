pipeline {
    agent any

    tools {
        maven 'Maven 3.9.9' // Make sure this Maven is configured in Jenkins Global Tools
        jdk 'JDK 21'        // Same for JDK
    }
    
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                bat 'mvn clean install'
            }
        }

        stage('Test') {
            steps {
                bat 'mvn test'
            }
        }

        stage('Package') {
            steps {
                bat 'mvn package'
            }
        }

        stage('Deploy') {
            steps {
                bat 'echo Deploying application...'
                bat 'copy target\\basic-java-app-1.0-SNAPSHOT.jar C:\\path\\to\\deploy\\'
            }
        }
    }

    post {
        always {
            bat 'echo Cleaning up...'
        }

        success {
            bat 'echo Build succeeded!'
        }

        failure {
            bat 'echo Build failed!'
        }
    }
}
