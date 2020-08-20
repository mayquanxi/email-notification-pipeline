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
          mail to: 'mymail@gmail.com',
                 cc : 'ccedpeople@gamil.com'
                subject: "INPUT: Build ${env.JOB_NAME}", 
                body: "Awaiting for your input ${env.JOB_NAME} build no: ${env.BUILD_NUMBER} .Click below to promote to production\n${env.JENKINS_URL}job/${env.JOB_NAME}\n\nView the log at:\n ${env.BUILD_URL}\n\nBlue Ocean:\n${env.RUN_DISPLAY_URL}"
                timeout(time: 60, unit: 'MINUTES'){
                    input message: "Promote to Production?", ok: "Promote"
                }
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
      mail to: "mayquanxi@gmail.com", subject: "always send admin", body: "This is always run"
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
