pipeline {
    agent any
    
    environment {
        // SonarQube server configuration
        SONARQUBE_SERVER = 'http://localhost:9000'  // Replace with your SonarQube server URL if different
        SONARQUBE_TOKEN = 'sqp_0745c2e60c1bedf533a3ffa5be1ced7dbd89f4cf'  // Replace with your SonarQube token
    }

    stages {
        stage('Checkout') {
            steps {
                // Checkout the repository
                git 'https://github.com/ChaiMoo/SpringPetClinic.git'
            }
        }
        
        stage('SonarQube Analysis') {
            steps {
                script {
                    // Run the SonarQube analysis using Maven
                    sh """
                        mvn clean verify sonar:sonar \
                          -Dsonar.projectKey=exercice \
                          -Dsonar.host.url=${SONARQUBE_SERVER} \
                          -Dsonar.login=${SONARQUBE_TOKEN}
                    """
                }
            }
        }
        
        // Add additional stages here (for Unit Tests, Functional Tests, etc.)
    }
    
    post {
        success {
            echo 'SonarQube analysis completed successfully.'
        }
        failure {
            echo 'SonarQube analysis failed.'
        }
    }
}
