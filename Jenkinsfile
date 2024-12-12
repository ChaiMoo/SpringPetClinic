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
                sh './mvnw clean install'  // Maven build command
            }
        }
    }
}
