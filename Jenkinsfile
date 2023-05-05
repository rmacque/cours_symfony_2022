pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        echo 'stage Build'
        sh 'echo \'edition pipeline\''
      }
    }

    stage('test') {
      parallel {
        stage('unitaire') {
          steps {
            sh 'php bin/phpunit tests/unit'
          }
        }

        stage('integration') {
          steps {
            sh 'php bin/phpunit tests/integration'
          }
        }

        stage('fonctionnel') {
          steps {
            sh 'php bin/phpunit tests/fonctionnel'
          }
        }

      }
    }

    stage('deploy') {
      steps {
        sh 'symfony server:start'
      }
    }

  }
}