pipeline {
    agent any   // يشتغل على أي Agent متاح

    environment {
        DOCKER_REGISTRY = "my-dockerhub"
        IMAGE_NAME = "solar-system"
    }

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main',
                    url: 'http://git-server:5555/dasher-org/solar-system.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Run Tests') {
            steps {
                sh 'npm test'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh "docker build -t ${DOCKER_REGISTRY}/${IMAGE_NAME}:${BUILD_ID} ."
            }
        }

        stage('Push to Registry') {
            steps {
                withDockerRegistry([credentialsId: 'docker-hub-credentials', url: '']) {
                    sh "docker push ${DOCKER_REGISTRY}/${IMAGE_NAME}:${BUILD_ID}"
                }
            }
        }
    }

    post {
        success {
            echo "✅ Build and Deploy succeeded!"
        }
        failure {
            echo "❌ Build failed!"
        }
    }
}

