pipeline{
    agent{
        dockerfile{
            filename 'Dockerfile-cicd'
            args '-u 0:0 --net host --privileged -v /var/rundocker.sock:/var/run/docker.sock'
        }
    }
    options{
        timestamps()
    }
    environment{
        SONAR_SCANNER_PATH = '/opt/sonar-scanner/bin/sonar-scanner'
        SONARQUBE_LOGIN_SECRET = ''
    }
    stages{
        stage('Sonarqube Analysis'){
            steps{
                script{
                    withSonarQubeEnv('SonarQube'){
                        sh '''
                        ${SONAR_SCANNER_PATH} -Dsonar.login=${SONARQUBE_LOGIN_SECRET}
                        '''
                    }
                }
            }
        }
        stage('Quality-gate'){
            steps{
                withSonarQubeEnv('SonarQube'){
                    timeout(time: 1, unit: 'HOURS'){
                        sh '''
                        waitForQualityGate abortPipeline: false
                        '''
                    }
                }
            }
        }
    }
}