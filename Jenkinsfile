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
      mail to: "mayquanxi@gmail.com", subject: "you have ran successful ${env.JOB_NAME}", body: "This will run only if successful ${env.BUILD_URL}"
    }
    always {
      echo 'This is always run'
      deleteDir()
      emailext to: "mayquanxi@gmail.com", cc: "mayquanxi@gmail.com" subject: "always send admin", recipientProviders: [[$class: 'DevelopersRecipientProvider'], [$class: 'RequesterRecipientProvider']], body: "This is always run"
    }
    failure {
      echo 'This will run only if failed'
      mail to: "mayquanxi@gmail.com", subject: "Failed Pipeline", body: "his will run only if failed"
      }
    unstable {
      echo 'This will run only if the run was marked as unstable'
      mail to: "mayquanxi@gmail.com", subject: "Failed Pipeline", body: "This will run only if the run was marked as unstable"
    }
  }
}
