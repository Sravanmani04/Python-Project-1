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
                        sh '''
                        echo "Git Url = ${GIT_URL}"
                        echo "Git Branch = ${GIT_BRANCH}"
                        echo "Author Name = ${GIT_AUTHOR_NAME}"
                        echo "Commiter Name = ${GIT_COMMITTER_NAME}"
                        echo "Build ID = ${BUILD_ID}"
                        echo "Build Number = ${BUILD_NUMBER}"
                        echo "Jenkins Workspace Directory = ${WORKSPACE}"
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