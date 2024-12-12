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
                    sh './mvnw sonar:sonar -Dsonar.projectKey=${SONAR_PROJECT_KEY} -Dsonar.host.url=${SONAR_HOST_URL}'
                }
            }
        }

        stage('Build and Unit Tests') {
            steps {
                script {
                    // Clean, compile, and run unit tests with Maven
                    sh './mvnw clean install'
                }
            }
        }

        // Next steps can be added here like functional tests, reports, and notifications
    }
}
