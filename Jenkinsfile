pipeline {
  agent {
    node {
      label 'centos-docker'
    }

  }
  stages {
    stage('checkout code') {
      steps {
        git(url: 'https://github.com/lidorg-dev/docker-demo.git', branch: 'master', poll: true, credentialsId: 'git-creds')
      }
    }

    stage('docker build') {
      parallel {
        stage('docker build') {
          steps {
            sh "docker build -t node-app:${env.BUILD_ID} ."
          }
        }

        stage('test') {
          steps {
            sh 'npm install && npm test'
          }
        }

      }
    }

    stage('docker publish') {
      steps {
        sh "docker tag node-app:${env.BUILD_ID} lidorlg/node-app:${env.BUILD_ID} && docker push lidorlg/node-app:${env.BUILD_ID}"
      }
    }

    stage('chuck norris') {
      steps {
        chuckNorris()
      }
    }

  }
}