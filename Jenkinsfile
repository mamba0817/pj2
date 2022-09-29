pipeline {
  agent any
  stages {
    stage('git scm update') {
      steps {
        git url: 'http://github.com/mamba0817/pj2', branch: 'main'
      }
    }
    stage('docker build and push') {
      steps {
        sh '''
        sudo docker build -t leeansin/myweb:1.2 .
        sudo docker push leeansin/myweb:1.2
        '''
      }
    }
    stage('deploy k8s') {
      steps {
        sh '''
        sudo kubectl apply -f deploy.yml
        '''
      }
    }
  }
}
