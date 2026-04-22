pipeline {
    agent any

    tools {
        // These names MUST match Manage Jenkins -> Tools exactly
        jdk 'JDK17'     
        maven 'Maven3'  
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build & Test') {
            steps {
                // Use 'bat' for Windows Command Prompt
                bat 'mvn clean test'
            }
        }
    }

    post {
        always {
            // allowEmptyResults prevents the "Configuration error" if tests didn't run
            junit allowEmptyResults: true, testResults: '**/target/surefire-reports/*.xml'
        }
    }
}
