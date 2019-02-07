#!/bin/groovy

passed = []

def part(name, closure) {
  if (passed.contains(name)) {
    return
  }
  stage name
  try {
    closure.call()
    passed.add(name)
  } catch (e) {
    echo "===> part ${name} failed with ${e} <==="
    currentBuild.result = 'FAILURE'
  }
}

def go() {
  part('one') {sh 'sleep 5' echo 'first part passes'}
  part('two') {
    // Example of a flaky build step:
    if (env.BUILD_NUMBER == '2') {
      sh 'sleep 5'        
      echo 'second part passes'
    } else {
      sh 'sleep 5' 
      error 'second part fails'
    }
  }
  part('three') {sh 'sleep 5 'echo 'third part passes'}
}

go()
def origBuildNumber = env.BUILD_NUMBER // CJP-1620 workaround
checkpoint 'performed parts'
if (origBuildNumber != env.BUILD_NUMBER) {
    go()
}
