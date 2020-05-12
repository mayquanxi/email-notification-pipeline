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
    always {
      echo 'This is always run'
      deleteDir()
      mail to: 'mayquanxi@gmail.com', subject: 'always send admin: ${currentBuild.fullDisplayName}', body: 'jus has someone run pipeline'
    }
    success {
      echo 'This will run only if successful'
      mail to: 'khacmanhk45s1@gmail.com', subject: 'you have ran successful', body: 'you have ran successful'
    }
    failure {
      echo 'This will run only if failed'
      email to: 'khacmanhk45s1@gmail.com', subject: 'Failed Pipeline: ${currentBuild.fullDisplayName}', body: 'Something is wrong with ${env.BUILD_URL}'
    }
    unstable {
      echo 'This will run only if the run was marked as unstable'
      email to: 'khacmanhk45s1@gmail.com', subject: 'Failed Pipeline: ${currentBuild.fullDisplayName}', body: 'This will run only if the run was marked as unstable'
    }
    changed {
      echo 'This will run only if the state of the Pipeline has changed'
      echo 'For example, if the Pipeline was previously failing but is now successful'
      email to: 'khacmanhk45s1@gmail.com', subject: 'changed: ${currentBuild.fullDisplayName}', body: 'jus changed pipeline'
    }
  }
}
