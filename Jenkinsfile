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
        stage( 'stage1' ) { 
            agent any
            steps { 
                script {
                    sleep (5)
                    passed.add('name1') 
                }
            }  
        }  
        stage( 'ckpt' )  { 
            agent none
            steps { 
                checkpoint 'performed parts' 
            } 
        }
        stage( 'stage2' ) { 
            agent any
            steps {
            script {
                if( passed.contains('name1') )
                    echo 'it should work' 
                }  
            }
        }
    }
}

