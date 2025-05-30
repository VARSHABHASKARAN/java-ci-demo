pipeline {
    agent any

    tools {
        // Make sure Maven and JDK are installed and configured in Jenkins global tools
        maven 'Maven'  // The name configured in Jenkins for Maven
        jdk 'JDK'      // The name configured in Jenkins for JDK
    }

    stages {
        stage('Checkout SCM') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                // Use Windows batch command instead of sh
                bat 'mvn clean compile'
            }
        }

        stage('Test') {
            steps {
                bat 'mvn test'
            }
            post {
                always {
                    junit '**/target/surefire-reports/*.xml'
                }
            }
        }
    }

    post {
        success {
            echo 'Build and Tests completed successfully!'
        }
        failure {
            echo 'Build or Tests failed.'
        }
    }
}
