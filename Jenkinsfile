pipeline {
    agent any

    environment {
        DOCKERHUB_CREDENTIALS = credentials('docker-credentials') // Jenkins credentials ID
    }

    stages {
        stage("Clone code") {
            steps {
                echo "📥 Cloning code from GitHub"
                git url: 'https://github.com/Sakkthi27/django-notes-app.git', branch: 'main'
            }
        }

        stage("Build Docker Image") {
            steps {
                echo "🐳 Building Docker image for django_app"
                sh "docker build -t django_app:latest ."
            }
        }

        stage("Trivy Scan") {
            steps {
                echo "🔍 Scanning django_app image with Trivy"
                sh "trivy image django_app:latest --scanners vuln || true"
            }
        }

        stage("Login to DockerHub") {
            steps {
                echo "🔐 Logging in to DockerHub"
                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
            }
        }

        stage("Tag & Push Docker Image") {
            steps {
                echo "🚀 Tagging and pushing django_app to DockerHub"
                sh """
                    docker tag django_app:latest devski/django_app:latest
                    docker push devski/django_app:latest
                """
            }
        }

        stage("Run with Docker Compose") {
            steps {
                echo "🧹 Cleaning up old containers"
                sh "docker-compose down || true"

                echo "🚢 Deploying with docker-compose"
                sh "docker-compose up -d --build"
            }
        }

        stage("Health Check") {
            steps {
                echo "🩺 Checking if app is reachable"
                sh 'sleep 20'
                sh 'curl -f http://localhost || echo "App not reachable"'
            }
        }
    }

    post {
        success {
            echo "✅ Jenkins pipeline completed successfully!"
        }
        failure {
            echo "❌ Jenkins pipeline failed. Please check logs."
        }
    }
}
