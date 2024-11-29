pipeline {
    agent any

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
                sh 'docker push ahmedhanzala01/backend-app:v1'
                sh 'docker push ahmedhanzala01/frontend-app:v1'
            }
        }
        stage('Deploy') {
            steps {
                sh 'docker-compose up -d'
            }
        }
    }
}
