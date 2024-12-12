pipeline {
    agent any

    environment {
        SONARQUBE_URL = 'http://localhost:9000'
        SONARQUBE_AUTH_TOKEN = 'sqp_0745c2e60c1bedf533a3ffa5be1ced7dbd89f4cf'
        SONAR_PROJECT_KEY = 'exercice'
        MAVEN_HOME = '/opt/maven'  // Ensure this points to your Maven installation if needed
        PATH = "${MAVEN_HOME}/bin:${env.PATH}"
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/karoumbr/SpringPetClinic.git'
            }
        }
        
        stage('SonarQube Analysis') {
            steps {
                // Run SonarQube analysis after the build
                sh 'chmod +x ./mvnw'
                sh """
                ./mvnw clean verify sonar:sonar \
                  -Dsonar.projectKey=${SONAR_PROJECT_KEY} \
                  -Dsonar.host.url=${SONARQUBE_URL} \
                  -Dsonar.login=${SONARQUBE_AUTH_TOKEN}
                """
            }
        }

        stage('Build with Maven') {
            steps {
                // Ensure the Maven wrapper has executable permissions
                sh 'chmod +x ./mvnw'

                // Use the Maven Wrapper to build the project
                sh './mvnw clean install'  // Run Maven build command
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
