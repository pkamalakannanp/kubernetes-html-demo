pipeline {

  environment {
    registry = "kamal0405/cicd-html-demo"
<<<<<<< HEAD
=======
    registryCredential = 'docker_credentials'
>>>>>>> 07e42d4a325b7ce92646405ad7d2034da397f65e
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
          docker.withRegistry('https://registry.hub.docker.com', 'docker_credentials') {
            dockerImage.push()
          }
        }
      }
    }

    stage('Deploy App') {
      steps {
        script {
<<<<<<< HEAD
          withKubeConfig(caCertificate: '', clusterName: 'mypro', contextName: '', credentialsId: 'mykubeconfignew', namespace: '', serverUrl: 'http://127.0.0.1:58382/') {
    // some block
}
=======
          kubernetesDeploy(configs: "myweb.yaml", kubeconfigId: "mykubeconfignew")
>>>>>>> 07e42d4a325b7ce92646405ad7d2034da397f65e
        }
      }
    }

  }

}
