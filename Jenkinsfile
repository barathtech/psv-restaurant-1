pipeline {
    agent any

    environment {
        DOCKER_IMAGE = 'my-nginx-app'  // Define your Docker image name
        CONTAINER_NAME = 'my-nginx-container'  // Define your Docker container name
        PORT_MAPPING = '8081:80'  // Define your port mapping (host_port:container_port)
    }

    stages {
        stage('Build') {
            steps {
                script {
                    // Build Docker image
                    sh "docker build -t ${DOCKER_IMAGE} ."
                }
            }
        }

        stage('Deploy') {
            steps {
                script {
                    // Stop and remove existing container (if any)
                    sh "docker stop ${CONTAINER_NAME} || true"
                    sh "docker rm ${CONTAINER_NAME} || true"

                    // Run Docker container
                    sh "docker run -d --name ${CONTAINER_NAME} -p ${PORT_MAPPING} ${DOCKER_IMAGE}"
                }
            }
        }
    }

    post {
        success {
            echo 'Deployment successful!'
        }
        failure {
            echo 'Deployment failed!'
        }
    }
}
