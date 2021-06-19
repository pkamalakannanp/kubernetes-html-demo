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
          docker.withRegistry( 'https://registry.hub.docker.com', 'docker_credentials' ) {
            dockerImage.push()
          }
        }
      }
    }

    stage('Deploy App') {
      steps {
        script {
         kubeconfig(credentialsId: 'mykubeconfignew', serverUrl: '')
         kubernetesDeploy(configs: "myweb.yaml", kubeconfigId: "mykubeconfignew") {
    // some block
}
        }
      }
    }

  }

}
