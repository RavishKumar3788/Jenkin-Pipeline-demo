pipeline {
    agent any
    stages {
        stage('Docker Info') {
            steps {
                echo 'Gathering Docker information...'
                sh 'docker version'
                sh 'docker ps'
            }
        }
    }
}
