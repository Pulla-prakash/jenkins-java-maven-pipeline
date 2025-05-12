pipeline {
    agent any

    tools {
        maven 'Maven 3.9.9' // Ensure this version is configured in Jenkins
        jdk 'JDK 21'      // Ensure this JDK version is configured in Jenkins
    }
    
    stages {
        stage('Checkout') {
            steps {
                // Checkout code from SCM
                checkout scm
            }
        }

        stage('Build') {
            steps {
                // Build the project using Maven
                bat 'mvn clean install'
            }
        }

        stage('Test') {
            steps {
                // Run unit tests
                bat 'mvn test'
            }
        }

        stage('Package') {
            steps {
                // Package the application
                bat 'mvn package'
            }
        }

        stage('Deploy') {
            steps {
                // Simple deployment example
                sh 'echo "Deploying application..."'
                // Example of copying artifacts to a deploy location
                sh 'cp target/basic-java-app-1.0-SNAPSHOT.jar /path/to/deploy/'
            }
        }
    }

    post {
        always {
            // Clean up actions
            sh 'echo "Cleaning up..."'
        }

        success {
            // Actions on successful build
            echo 'Build succeeded!'
        }

        failure {
            // Actions on failed build
            echo 'Build failed!'
        }
    }
}
