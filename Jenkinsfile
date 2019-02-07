#!/bin/groovy

passed = []

def part(name, closure) {
    if (!passed.contains(name)) {
      try {
        closure.call()
        passed.add(name)
      } catch (e) {
        echo "===> part ${name} failed with ${e} <==="
        currentBuild.result = 'FAILURE'
      }
    }
}

pipeline {
    agent none
        stages {
            stage( 'one' ) {
                    steps {
                part('one') {
                    sh '''
                        sleep 5
                        echo 'first part passes'
                    '''
                    }
            }
            }
            stage( 'one' ) {
                    steps {
                part('two') {
                  // Example of a flaky build step:
                  //if (env.BUILD_NUMBER == '2') {
                  //  sh 'sleep 5'        
                  //  echo 'second part passes'
                  //} else {
                    //echo env.BUILD_NUMBER
                    sh 'sleep 5' 
                    error 'second part fails'
                  //}
                }
            }
            }
            stage( 'one' ) {
                    steps {
                part('three') {
                    sh '''
                        sleep 5 
                        echo 'third part passes'
                    '''
                        }
            }
            }
            stage( 'last' ) {
                steps {
                    def origBuildNumber = env.BUILD_NUMBER // CJP-1620 workaround
                    checkpoint 'performed parts'
                }
            }
        }
            stages {
                stage( 'one' ) {
                    steps {
        if (origBuildNumber != env.BUILD_NUMBER) {
                    sh '''
                        sleep 5
                        echo 'first part passes'
                    '''
                    }
                }
                }
                stage( 'one' ) {
                    steps {
        if (origBuildNumber != env.BUILD_NUMBER) {
                        part('two') {
                          // Example of a flaky build step:
                          //if (env.BUILD_NUMBER == '2') {
                          //  sh 'sleep 5'        
                          //  echo 'second part passes'
                          //} else {
                    sh '''
                        sleep 5 
                        echo 'third part passes'
                    '''
                          //}
                        }
                    }
                }
                }
                stage( 'one' ) {
                    steps {
        if (origBuildNumber != env.BUILD_NUMBER) {
                        part('three') {
                    sh '''
                        sleep 5 
                        echo 'third part passes'
                    '''
                            }
                    }
                }
                }
            }
        }
}
