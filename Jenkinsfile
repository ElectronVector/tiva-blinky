pipeline {
    agent { dockerfile true }
    stages {
        stage('Unit Test') {
            steps {
                sh 'ceedling test:all'
            }
        }
    }
}