pipeline {
    agent any

    tools {
        jdk 'JDK17'     // Must match the name in Manage Jenkins -> Tools
        maven 'Maven3'  // Must match the name in Manage Jenkins -> Tools
    }

    stages {
        stage('Checkout') {
            steps {
                // This pulls code from the Git repo configured in the Job
                checkout scm
            }
        }

        stage('Build & Test') {
            steps {
                // Runs the tests and generates XML reports
                bat 'mvn clean test' 
            }
        }
    }

    post {
        always {
            // Tells Jenkins where to find the XML results to build the graph
            junit '**/target/surefire-reports/*.xml'
        }
    }
}
