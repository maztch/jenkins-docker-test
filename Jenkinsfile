pipeline {
  agent any
  stages {
    stage('Composer') {
            agent {
                docker { image 'composer' }
            }
            steps {
                install
            }
        }
  }
}