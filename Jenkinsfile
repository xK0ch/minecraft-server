pipeline {
    agent any

    stages {
        stage('Deploy') {
            steps {
                script {
                    sh 'docker compose -f docker-compose-minecraft-server.yml down'
                    sh 'docker image prune -af'
                    sh 'docker compose -f docker-compose-minecraft-server.yml up -d'
                }
            }
        }
    }
}