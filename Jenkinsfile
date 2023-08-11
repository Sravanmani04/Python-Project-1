pipeline{
    agent{
        label "slave"
    }
    environment{

    }
    stages{
        stage("Pipeline metadata"){
            steps{
                echo "========METADATA========"
                script{
                    try{
                        sh '''
                        echo "Git Url = $GIT_URL"
                        echo "Git Branch = $GIT_BRANCH"
                        '''
                    }
                    catch(Exception error){
                        echo "pipeline metadata check Failed: ${error.message}"
                        sh "exit 1"
                    }
                }
            }
        }
    }
}        