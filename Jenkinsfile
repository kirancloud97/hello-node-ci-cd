pipeline {
    agent any
    environment {
        DOCKER_IMAGE = 'kirancloud97/hello-node'
        DOCKER_CREDENTIALS_ID = 'docker-hub-creds'
    }
    stages {
        stage('Clone Repo') {
            steps {
                git 'https://github.com/kirancloud97/hello-node-ci-cd.git'
            }
        }
        stage('Build Docker Image') {
            steps {
                script {
                    docker.build(DOCKER_IMAGE)
                }
            }
        }
       stage('Push to Docker Hub') {
    steps {
        script {
            docker.withRegistry('https://index.docker.io/v1/', 'dockerhub') {
                sh 'docker tag kirancloud97/hello-node kirancloud97/hello-node:latest'
                sh 'docker push kirancloud97/hello-node:latest'
            }
        }
    }
}

        stage('Deploy Container') {
            steps {
                script {
                    sh 'docker rm -f hello-node || true'
                    sh "docker run -d -p 3000:3000 --name hello-node ${DOCKER_IMAGE}:latest"
                }
            }
        }
    }
}
