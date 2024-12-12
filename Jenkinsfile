pipeline {
    agent any
    environment {
        MAVEN_HOME = tool name: 'Maven 3', type: 'Tool'  // Specify the Maven tool you configured
    }
    stages {
        stage('Checkout Code') {
            steps {
                git 'https://github.com/ChaiMoo/SpringPetClinic.git'
            }
        }
        stage('Build with Maven') {
            steps {
                script {
                    // Compile the project with Maven
                    sh "'${MAVEN_HOME}/bin/mvn' clean install"
                }
            }
        }
    }
}

