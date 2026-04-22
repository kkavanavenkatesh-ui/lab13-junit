pipeline {
    agent any
    tools {
        jdk 'JDK17'     // Ensure this matches "Manage Jenkins > Tools"
        maven 'Maven3'  // Ensure this matches "Manage Jenkins > Tools"
    }
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Build & Test') {
            steps {
                // Use 'bat' for Windows, 'sh' is only for Linux
                bat 'mvn clean test'
            }
        }
    }
    post {
        always {
            // This records the results even if the build fails
            junit '**/target/surefire-reports/*.xml'
        }
    }
}
