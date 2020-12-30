pipeline {

 
  agent any

  stages {

    stage('Checkout Source') {
      steps {
        git 'https://github.com/veereshba1/jenkins.git'
      }
    }

    stage('Build image') {
      steps{
        script {
          dockerImage = docker.build("805054/new-repo:${env.BUILD_ID}")
           
        }
      }
    }

    stage('Push Image') {
      steps{
        script {
          docker.withRegistry('https://registry.hub.docker.com', 'Dockerhub') {
                            myapp.push("latest")
                            myapp.push("${env.BUILD_ID}")
          }
        }
      }
    }

    stage('Deploy App') {
      steps {
        script {
          kubernetesDeploy(configs: "myweb.yaml", kubeconfigId: "mykubeconfig")
        }
      }
    }

  }

}
