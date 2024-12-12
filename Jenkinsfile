pipeline {
    agent any

    environment {
        SONARQUBE = 'SonarQube' // This is the SonarQube server name from Jenkins configuration
        SONAR_HOST_URL = 'http://your_sonarqube_server_url'
        SONAR_PROJECT_KEY = 'SpringPetClinic'
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/karoumbr/SpringPetClinic.git'
            }
        }

        stage('SonarQube Analysis') {
            steps {
                script {
                    // Run SonarQube analysis using Maven
                    // Ensure the mvnw script has execute permissions
                    sh 'chmod +x ./mvnw'
                    sh './mvnw sonar:sonar -Dsonar.projectKey=${SONAR_PROJECT_KEY} -Dsonar.host.url=${SONAR_HOST_URL}'
                }
            }
        }

        stage('Build and Unit Tests') {
            steps {
                script {
                    // Clean, compile, and run unit tests with Maven
                    // Ensure the mvnw script has execute permissions
                    sh 'chmod +x ./mvnw'
                    sh './mvnw clean install'
                }
            }
        }

        // You can add more stages here for additional steps like functional tests, reports, and notifications
    }
}
