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
                    catch(Exception emy){
                        echo "pipeline metadata check Failed: ${emy.message}"
                        sh "exit 1"
                    }
                }
            }
        }
    }
}        