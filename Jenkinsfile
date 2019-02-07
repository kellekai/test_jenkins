//def part(name, closure) {
//  if (passed.contains(name)) {
//    return
//  }
//  stage name
//  try {
//    closure.call()
//    passed.add(name)
//    currentBuild.result = 'SUCCESS'
//  } catch (e) {
//    echo "===> part ${name} failed with ${e} <==="
//    //currentBuild.result = 'FAILURE'
//  }
//}

passed = []
pipeline {
    agent none
    stages{
    stage( 'stage' ) { 
        steps { 
            script {
                sleep (5)
                passed.add('name1') 
            }
        }  
    }  
    stage( 'ckpt' )  { steps { checkpoint 'performed parts' } }
    stage( 'stage' ) { 
        steps {
        script {
            if( passed.contains('name1') )
                echo 'it should work' 
            }  
        }
    }
}

