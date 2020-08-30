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
      emailext to: "khacmanhk45s1@gmail.com", subject: "you have ran successful ${env.JOB_NAME}", body: "This will run only if successful ${env.BUILD_URL}"
    }
    always {
      echo 'This is always run'
      deleteDir()
      emailext ( 
        body: '''
          This is mail test
          Jobs Name: ${env.JOB_NAME}
          Build Number: ${env.BUILD_NUMBER}
          ''',
        recipientProviders: [developers()], 
        subject: 'TEST MAIL', 
        to: 'khacmanhk45s1@gmail.com' 
      )
    }
    failure {
      echo 'This will run only if failed'
      mail to: "khacmanhk45s1@gmail.com", subject: "Failed Pipeline", body: "his will run only if failed"
      }
    unstable {
      echo 'This will run only if the run was marked as unstable'
      mail to: "khacmanhk45s1@gmail.com", subject: "Failed Pipeline", body: "This will run only if the run was marked as unstable"
    }
  }
}
