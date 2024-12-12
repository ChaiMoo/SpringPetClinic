pipeline {
    agent any
    environment {
        SONARQUBE_URL = 'http://localhost:9000' // Replace with your SonarQube server's URL
        SONARQUBE_TOKEN = credentials('token') // Replace 'sonar-token' with your Jenkins credential ID
    }
    stages {
        stage('Checkout Code') {
            steps {
                checkout scm
            }
        }
        stage('Static Code Analysis with SonarQube') {
            steps {
                withSonarQubeEnv('Sonarqube') { // Replace 'SonarQube' with your SonarQube server configuration name
                    sh """
                        sonar-scanner \
                        -Dsonar.projectKey=SpringPetClinic \
                        -Dsonar.sources=src \
                        -Dsonar.java.binaries=target/classes \
                        -Dsonar.host.url=$SONARQUBE_URL \
                        -Dsonar.login=$SONARQUBE_TOKEN
                    """
                }
            }
        }
    }
    post {
        always {
            echo 'Pipeline execution completed!'
        }
    }
}
