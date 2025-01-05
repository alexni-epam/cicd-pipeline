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
        sh 'docker build -t ani_ci_cd_testimage'
      }
    }

    stage('Push to Docker Hub') {
      steps {
        script {
          docker.withRegistry('https://registry.hub.docker.com', 'docker_hub_creds_id')
          {
            app.push("${env.BUILD_NUMBER}")
            app.push("latest")
          }
        }

      }
    }

  }
}