pipeline {

  agent { label 'kubepod' }
  
  stages {

    stage('Checkout Source') {
      steps {
        git url:'https://github.com/veereshba1/jenkins.git', branch:'main'
      }
    }

    stage('Deploy App') {
      steps {
        script {
          kubernetesDeploy(configs: "nginx.yaml", kubeconfigId: "mykubeconfig")
        }
      }
    }

  }

}
