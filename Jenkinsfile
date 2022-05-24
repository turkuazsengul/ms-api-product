pipeline {
  agent any
  stages {
    stage('Maven Install') {
      steps {
        sh 'mvn clean install'
      }
    }
    stage('Docker Build') {
      steps {
        sh 'docker build -f Dockerfile -t turkuazsengul/ms-api-product:latest .'
      }
    }
    stage('Docker Push') {
      steps {
        sh 'docker push turkuazsengul/ms-api-user:latest'
      }
     }
  }
}