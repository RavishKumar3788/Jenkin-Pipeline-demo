pipeline {
    agent any
    
    stages {
        stage('Run in Docker') {
            steps {
                sh '''#!/bin/bash
                    docker run --rm -v "$PWD":/app -w /app mcr.microsoft.com/dotnet/sdk:8.0 bash -c "dotnet --version"
                '''
            }
        }
    }

    stages {
        stage('Clone') {
            steps {
                git branch: 'master',
                    url: 'https://github.com/RavishKumar3788/Jenkin-Pipeline-demo.git'
            }
        }
        stage('Build') {
            steps {
                sh 'dotnet build WebApiForDocker.sln'
            }
        }
        // stage('Test') {
        //     steps {
        //         sh 'dotnet test'
        //     }
        // }
        stage('Publish') {
            steps {
                sh 'dotnet publish -c Release'
            }
        }
    }
}