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
    stage( 'stage' ) { steps { sleep (5); script { passed.add('name1') } }  }  
    stage( 'stage' ) { steps { sleep (5); script { passed.add('name2') } }  } 
    stage( 'stage' ) { steps { sleep (5); script { passed.add('name3') } }  } 
    stage( 'stage' ) { steps { sleep (5); script { passed.add('name4') } }  } 
    stage( 'stage' ) { steps { sleep (5); script { passed.add('name5') } }  } 
    stage( 'ckpt' )  { steps { checkpoint 'performed parts' } }
    stage( 'stage' ) { 
        steps { 
        if( passed.contains('name1') )
            echo 'it should work' 
            }  
        }  
    }
}

