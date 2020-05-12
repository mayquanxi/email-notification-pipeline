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
          sh 'echod "this is stage Test"'
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
      mail to: "mayquanxi@gmail.com", subject: "always send admin", body: "jus has someone run pipeline"
    }
    failure {
      echo 'This will run only if failed'
      mail to: "mayquanxi@gmail.com", subject: "Failed Pipeline", body: "Something is wrong with"
      }
    unstable {
      echo 'This will run only if the run was marked as unstable'
      mail to: "khacmanhk45s1@gmail.com", subject: "Failed Pipeline", body: "This will run only if the run was marked as unstable"
    }
  }
}
