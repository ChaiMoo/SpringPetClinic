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
        


        stage('Functional Tests with Robot Framework') {
            steps {
                script {
                    // Run functional tests with Robot Framework
                    sh 'robot tests/functional/FindOwners.robot'  // Replace with your actual test file paths
                    sh 'robot tests/functional/VeterinariansList.robot'  // Replace with your actual test file paths
                }
            }
        }

    }

}
