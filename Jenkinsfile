pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: 'master']],
                          userRemoteConfigs: [[url: 'https://github.com/ChaiMoo/SpringPetClinic.git']]])
            }
        }
        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('SonarQube') { // Use the SonarQube configuration name
                    sh '''
                    sonar-scanner \
                    -Dsonar.projectKey=SpringPetClinic \
                    -Dsonar.sources=src \
                    -Dsonar.host.url=http://<sonarqube_server_ip>:9000 \
                    -Dsonar.login=<sonar_token>
                    '''
                }
            }
        }
    }
}
