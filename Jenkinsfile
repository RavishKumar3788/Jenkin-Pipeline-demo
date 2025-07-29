pipeline {
    agent any

    environment {
        ImageRepository = 'ravishchauhan/my-repo'
        EC2_IP = '13.126.174.46'
        DOCKER_COMPOSE_FILE = 'docker-compose.yml'
        ENV_FILE = '.env'
        DOCKER_IMAGE = "ravishchauhan/my-repo:latest"
        DOCKERHUB_CREDENTIALS = credentials('dockerhub-credentials') // Jenkins secret
    }

    stages {
        stage('Build Docker Image') {
            steps {
                script {
                    // build docker image with the help of docker compose file
                    echo "Building Docker image for ${ENV_FILE.ASPNETCORE_ENVIRONMENT} environment"
                    sh "docker-compose -f ${DOCKER_COMPOSE_FILE} build"
                    sh "docker-compose -f ${DOCKER_COMPOSE_FILE} up -d"
                    
                    // sh "docker build -t ${ImageRepository}/${JOB_NAME}:${BUILD_NUMBER} ."
                    // sh "docker tag ${ImageRepository}/${JOB_NAME}:${BUILD_NUMBER} ${DOCKER_IMAGE}"
                    // echo "Docker image built: ${ImageRepository}/${JOB_NAME}:${BUILD_NUMBER}"
                    sh "docker images"
                }
            }
        }
        // stage('Push Docker Image') {
        //     steps {
        //         script {
                   
        //             echo "Pushing Docker image to Docker Hub"
        //             // Login to Docker Hub
        //             withCredentials([usernamePassword(credentialsId: 'docker-login', usernameVariable: 'DOCKERHUB_USERNAME', passwordVariable: 'DOCKERHUB_PASSWORD')]) {
        //                 sh "echo ${DOCKERHUB_PASSWORD} | docker login -u ${DOCKERHUB_USERNAME} --password-stdin"
        //             }
        //             docker.withRegistry('https://index.docker.io/v1/', env.DOCKERHUB_CREDENTIALS) {
        //                 docker.image("${ImageRepository}/${JOB_NAME}:${BUILD_NUMBER}").push()
        //             }
        //         }
        //     }
        // }
        // stage('Deploy with Docker Compose') {
        //     steps {
        //         sh 'docker compose down || true'
        //         sh "docker compose pull"
        //         sh "docker compose up -d"
        //     }
        // }
    }
}