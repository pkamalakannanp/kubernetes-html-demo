pipeline {

  environment {
    registry = "kamal0405/cicd-html-demo"
    dockerImage = ""
  }

  agent any

  stages {

    stage('Checkout Source') {
      steps {
        git 'https://github.com/justmeandopensource/playjenkins.git'
      }
    }

    stage('Build image') {
      steps{
        script {
          dockerImage = docker.build registry + ":$BUILD_NUMBER"
        }
      }
    }

    stage('Push Image') {
      steps{
        script {
          docker.withRegistry( "" ) {
            dockerImage.push()
          }
        }
      }
    }

    stage('Deploy App') {
      steps {
        script {
          withKubeConfig(caCertificate: '', clusterName: 'mypro', contextName: '', credentialsId: 'mykubeconfignew', namespace: '', serverUrl: 'http://127.0.0.1:58382/') {
    // some block
}
        }
      }
    }

  }

}
