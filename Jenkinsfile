pipeline {
    agent any
    stages {
        stage('Docker Info') {
            steps {
                sh 'docker version'
                sh 'docker ps'
            }
        }
    }
}
