pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Jenkins هيعمل checkout للـ repo اللي فيه Jenkinsfile
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo "🔨 Building the project..."
                sh 'echo "Simulating build step"'
            }
        }

        stage('Test') {
            steps {
                echo "🧪 Running tests..."
                sh 'echo "Simulating tests step"'
            }
        }

        stage('Deploy') {
            steps {
                echo "🚀 Deploying application..."
                sh 'echo "Simulating deploy step"'
            }
        }
    }

    post {
        success {
            echo "✅ Build succeeded!"
        }
        failure {
            echo "❌ Build failed!"
        }
    }
}

