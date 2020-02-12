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
      steps {
        sh '"docker build -t node-app:${env.BUILD_ID} ."'
      }
    }

  }
}