pipeline {
  agent any

  options {
    disableConcurrentBuilds()
    timestamps()
    buildDiscarder(logRotator(numToKeepStr: '20'))
  }

  triggers {
    cron('H 4 * * *')
  }

  environment {
    HOST_USER = credentials('MINECRAFT_HOST_USER')
  }

  stages {
    stage('Deploy') {
      steps {
        sh 'docker compose -f docker-compose-minecraft-server.yml pull'
        sh 'docker compose -f docker-compose-minecraft-server.yml up -d --force-recreate'
      }
    }
  }

  post {
    always {
      sh 'docker image prune -f'
    }
  }
}
