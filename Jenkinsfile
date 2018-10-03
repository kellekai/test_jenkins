pipeline {
  agent any
  stages {
    stage('1-success_stage') {
      steps {
        sh 'echo "success stage"'
      }
    }
    stage('2-fail_stage') {
      steps {
          catchError {
              sh 'echo "fail_stage"'
              sh 'exit 255'
          }
      }
    }
    stage('3-success_stage') {
      steps {
        sh 'echo "success_stage"'
      }
    }
  }
}
