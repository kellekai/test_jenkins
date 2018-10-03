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
              sh 'TMPENV1="blabla" TMPENV2="blabla" exit 255'
          }
          catchError {
              sh 'TMPENV1="blabla" TMPENV2="blabla"'
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
