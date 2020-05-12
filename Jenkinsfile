pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'echo "this is stage Build"'
      }
    }
    stage('Test') {
      steps {
        sh 'echo "this is stage Test"'
        sh 'whoami'
      }
    }
  }
  post {
    
    success {
      echo 'This will run only if successful'
      mail to: "khacmanhk45s1@gmail.com", subject: "you have ran successful", body: "you have ran successful"
    }
    always {
      echo 'This is always run'
      deleteDir()
      mail to: "mayquanxi@gmail.com", subject: "always send admin: ${currentBuild.fullDisplayName}", body: "jus has someone run pipeline"
    }
  }
}
