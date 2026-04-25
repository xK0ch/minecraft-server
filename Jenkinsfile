pipeline {
  agent any

  options {
    disableConcurrentBuilds()
    timestamps()
    buildDiscarder(logRotator(numToKeepStr: '20'))
  }

  environment {
    HOST_USER = credentials('MINECRAFT_HOST_USER')
  }

  stages {
    stage('Deploy') {
      steps {
        sh 'docker compose -f docker-compose-minecraft-server.yml up --build -d --remove-orphans'
      }
    }
  }

  post {
    always {
      sh 'docker image prune -f'
    }
  }
}
