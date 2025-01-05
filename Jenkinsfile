pipeline {
  agent any
  stages {
    stage('Start build.sh') {
      agent any
      steps {
        sh 'script script/build.sh'
      }
    }

    stage('Start test.sh') {
      steps {
        sh 'script script/test.sh'
      }
    }

    stage('Build Docker Image') {
      steps {
        sh 'docker build -t mybuildimage'
      }
    }

  }
}