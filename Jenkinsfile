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
              STEP ONE : { sh 'echo "fail_stage"' }
              STEP TWO : { sh 'exit 255' }
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
