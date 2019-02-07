passed = []
def part(name, closure) {
  if (passed.contains(name)) {
    return
  }
  stage name
  try {
    closure.call()
    passed.add(name)
    currentBuild.result = 'SUCCESS'
  } catch (e) {
    echo "===> part ${name} failed with ${e} <==="
    //currentBuild.result = 'FAILURE'
  }
}
def go() {
  part('one')   { sleep (5) }
  part('two')   { sleep (5) }
  part('three') { sleep (5) }
  part('four')  { sleep (5) }
  part('five')  { sleep (5) }
  //part('two') {
  //   sh '''
  //   sleep 5
  //    echo 'first part passes'
  //   '''
  //    }
  ////part('two') {
  ////  // Example of a flaky build step:
  ////  if (env.BUILD_NUMBER == '25') {
  ////    echo 'second part passes'
  ////  } else {
  ////    error 'second part fails'
  ////  }
  ////}
  //part('three') {
  //   sh '''
  //   sleep 5
  //    echo 'third part passes'
  //   '''
  //    }
  //part('four') {
  //   sh '''
  //   sleep 5
  //    echo 'third part passes'
  //   '''
  //    }
}
go()
//def origBuildNumber = env.BUILD_NUMBER // CJP-1620 workaround
//checkpoint 'performed parts'
if (origBuildNumber != env.BUILD_NUMBER) {
  part('foo') { echo 'success' }
}
