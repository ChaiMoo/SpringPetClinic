pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: 'master']],
                          userRemoteConfigs: [[url: 'https://github.com/ChaiMoo/SpringPetClinic.git']]])
            }
        }
    }
}
