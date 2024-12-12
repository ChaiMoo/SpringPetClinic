pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/ChaiMoo/SpringPetClinic.git'
            }
        }
        stage('Build') {
            steps {
                // Ensure the Maven wrapper has executable permissions
                sh 'chmod +x ./mvnw'
                sh './mvnw clean install'  // Run Maven build command
            }
        }
    }
}
