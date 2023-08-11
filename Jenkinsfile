pipeline{
    agent{
        label "slave"
    }
    stages{
        stage("Pipeline metadata"){
            steps{
                echo "========METADATA========"
                script{
                    try{
                       sh "exit 1"
                    }
                    catch(Exception e){
                        echo "pipeline metadata check Failed: ${e.message}"
                        sh "exit 1"
                    }
                }
            }
        }
    }
}        