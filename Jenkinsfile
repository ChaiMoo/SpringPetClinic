pipeline {
    agent any

    environment {
        SONARQUBE_URL = 'http://localhost:9000'
        SONARQUBE_AUTH_TOKEN = 'sqp_0745c2e60c1bedf533a3ffa5be1ced7dbd89f4cf'
        SONAR_PROJECT_KEY = 'exercice'
        MAVEN_HOME = '/opt/maven'
        PATH = "${MAVEN_HOME}/bin:${env.PATH}"
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/ChaiMoo/SpringPetClinic.git'
            }
        }

        stage('Functional Tests with Robot Framework') {
            steps {
                script {
                    // Run functional tests in headless mode
                    sh 'xvfb-run -a robot tests/functional/FindOwners.robot'
                }
            }
        }
    }

    post {
        always {
            // Archive Robot Framework results
            archiveArtifacts artifacts: 'tests/functional/report.html'
        }

        success {
            echo 'Functional tests passed!'
        }

        failure {
            echo 'Functional tests failed.'
        }
    }
}
