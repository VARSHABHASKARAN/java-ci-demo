pipeline {
    agent any
    tools {
        maven 'Maven3'  // This should match your Maven name in Jenkins Global Tool Configuration
        jdk 'JDK17'     // This should match your JDK name in Jenkins Global Tool Configuration
    }
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/VARSHABHASKARAN/java-ci-demo.git'

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
    }
    post {
        always {
            junit '**/target/surefire-reports/*.xml'
            archiveArtifacts artifacts: '**/target/*.jar', allowEmptyArchive: true
        }
    }
}
