pipeline {
    agent any
    stages {
        stage('Verify Environment') {
            steps {
                script {
                    sh 'echo $SONAR_SCANNER_HOME'
                    sh 'echo $PATH'
                }
            }
        }
    }
}
