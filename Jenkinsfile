pipeline {
  agent {
    docker 'php:7.2-fpm'
  }
  stages {
    stage('build') {
      steps {
        sh 'php --version'
      }
    }
  }
}