pipeline {
  agent any
  stages {
    stage('BUILD') {
      steps {
        sh 'echo "success stage"'
      }
    }
    stage('TESTS') {
      steps {
        catchError() {
          sh 'TMPENV1="blabla" TMPENV2="blabla" exit 255'
        }

        catchError() {
          sh 'TMPENV1="blabla" TMPENV2="blabla" sleep 2'
        }

        catchError() {
          sh 'TMPENV1="blabla" TMPENV2="blabla" sleep 2'
        }

        catchError() {
          sh 'TMPENV1="blabla" TMPENV2="blabla" exit 255'
        }

        catchError() {
          sh 'TMPENV1="blabla" TMPENV2="blabla" sleep 2'
        }

        catchError() {
          sh 'TMPENV1="blabla" TMPENV2="blabla" sleep 2'
        }

      }
    }
    stage('FINALIZE') {
      steps {
        sh 'echo "success_stage"'
      }
    }
  }
}