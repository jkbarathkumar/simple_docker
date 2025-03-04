pipeline {
    agent any

    environment {
        DOCKER_IMAGE = 'barathkumar29/my-flask-app2:latest'
    }

    stages {
        stage('Clone Repository') {
            steps {
                git url:'https://github.com/jkbarathkumar/simple_docker.git',branch: 'main'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $DOCKER_IMAGE .'
            }
        }

        stage('Push Docker Image') {
            steps {
                withDockerRegistry([credentialsId: 'docker-hub-credentials', url: 'https://index.docker.io/v1/']) {
                    sh 'docker push $DOCKER_IMAGE'
                }
            }
        }
    }
}
