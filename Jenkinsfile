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
      environment {
        BUILD_ID = ''
      }
      steps {
        sh 'docker build -t node-app:latest .'
      }
    }

  }
}