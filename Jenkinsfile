nodejs repository
Insert the Build and Push Image stage after the existing Test stage and note the beforeAgent true option - this setting will result in the when condition being evaluated before acquiring and entering an agent for the stage. The branch condition is a built-in condition that allows executing stages only for specific branches - in this case the Build and Push Image stage will only execute for the master branch. The entire Pipeline shoud match what is below:
pipeline {
  agent none
  options { 
    buildDiscarder(logRotator(numToKeepStr: '2'))
    skipDefaultCheckout true
  }
  stages {
    stage('Test') {
      agent { label 'nodejs-app' }
      steps {
        checkout scm
        container('nodejs') {
          echo 'Hello World!'   
          sh 'node --version'
        }
      }
    }
    stage('Build and Push Image') {
      when {
         beforeAgent true
         branch 'master'
      }
      steps {
         echo "TODO - build and push image"
      }
    }
  }
}
