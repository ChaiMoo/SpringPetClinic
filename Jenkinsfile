pipeline {
    agent any

    environment {
        // Set the SonarQube environment variables
        SONARQUBE_URL = 'http://localhost:9000'
        SONARQUBE_AUTH_TOKEN = 'sqp_0745c2e60c1bedf533a3ffa5be1ced7dbd89f4cf'
        SONAR_PROJECT_KEY = 'exercice'
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/karoumbr/SpringPetClinic.git'
            }
        }

        stage('Build with Maven') {
            steps {
                // Ensure the Maven wrapper has executable permissions
                sh 'chmod +x ./mvnw'

                // Use the Maven Wrapper to build the project
                sh './mvnw clean install'  // If you're using Maven Wrapper
                // sh 'mvn clean install'  // If Maven is installed globally
            }
        }

        stage('SonarQube Analysis') {
            steps {
                // Run SonarQube analysis after the build
                sh """
                mvn clean verify sonar:sonar \
                  -Dsonar.projectKey=${SONAR_PROJECT_KEY} \
                  -Dsonar.host.url=${SONARQUBE_URL} \
                  -Dsonar.login=${SONARQUBE_AUTH_TOKEN}
                """
            }
        }
    }

    post {
        success {
            echo 'SonarQube analysis succeeded!'
        }
        failure {
            echo 'SonarQube analysis failed!'
        }
    }
}
