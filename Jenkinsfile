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
          script {
              try {
                sh 'echo "fail_stage"'
                sh 'exit 255'
              } catch (err) {
                  echo err
              }
              echo currentBuild.result
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
