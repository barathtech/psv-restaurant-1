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
                    sh "docker build -t nginx-app
                }
            }
        }

        stage('Deploy') {
            steps {
                script {
                    // Stop and remove existing container (if any)
                    sh "docker stop nginx-test || true"
                    sh "docker rm nginx-test || true"

                    // Run Docker container
                    sh "docker run -d --name nginx-test -p 89 nginx-test "
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
