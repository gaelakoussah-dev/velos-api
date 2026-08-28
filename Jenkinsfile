pipeline {
    agent any
    environment {
        REGISTRY_CREDENTIALS = credentials('docker-hub-credentials')
        IMAGE_NAME = "gakh00/velos-api"
    }
    stages {
        stage('Tester') {
            steps {
                sh 'python -m venv venv'
                sh './venv/Scripts/pip install -r requirements.txt pytest'
                sh './venv/Scripts/pytest tests/'
            }
        }
        stage('Construire') {
            steps {
                script {
                    env.IMAGE_TAG = "\"
                    sh "docker build -t \:\ -t \:latest ."
                }
            }
        }
        stage('Publier') {
            steps {
                script {
                    sh "echo \ | docker login -u \ --password-stdin"
                    sh "docker push \:\"
                    sh "docker push \:latest"
                }
            }
        }
        stage('Déployer') {
            steps {
                sh "kubectl set image deployment/velos-api velos-api=\:\"
                sh "kubectl rollout status deployment/velos-api"
            }
        }
    }
}
