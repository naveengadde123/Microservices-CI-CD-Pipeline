pipeline {
    agent any

    environment {
        IMAGE_NAME = "naveen/microservice"
    }

    stages {

        stage('Clone Repository') {
            steps {
                git 'https://github.com/naveengadde123/Microservices-CI-CD-Pipeline.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $IMAGE_NAME .'
            }
        }

        stage('Push Image') {
            steps {
                sh 'docker push $IMAGE_NAME'
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                sh 'kubectl apply -f k8s/deployment.yaml'
                sh 'kubectl apply -f k8s/service.yaml'
            }
        }

    }
}