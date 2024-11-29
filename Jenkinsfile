pipeline {
    agent any
    environment {
        DOCKER_USERNAME = 'ahmedhanzala01'
        DOCKER_PASSWORD = 'Hanzala5916'
        DOCKER_REGISTRY = 'https://index.docker.io/v1/'
    }
    stages {
        stage('Build Backend') {
            steps {
                sh 'cd backend && docker build -t ahmedhanzala01/backend-app:v1 .'
            }
        }
        stage('Build Frontend') {
            steps {
                sh 'cd frontend && docker build -t ahmedhanzala01/frontend-app:v1 .'
            }
        }
        stage('Push Images') {
            steps {
                sh 'echo ${DOCKER_PASSWORD} | docker login -u ${DOCKER_USERNAME} --password-stdin'
                sh 'docker push ahmedhanzala01/backend-app:v1'
                sh 'docker push ahmedhanzala01/frontend-app:v1'
            }
        }
        stage('Deploy') {
            steps {
                sh 'echo "" | sudo -S apt-get update && echo "" | sudo -S apt-get install -y docker-compose'
                sh 'docker-compose up -d'
            }
        }
    }
}
