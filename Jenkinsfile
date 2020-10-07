pipeline {
    agent any 
    stages {
        //environment {
        //    COMMIT = sh(git rev-parse HEAD)
        //    DATE = sh(date '+%Y%m%d%H%M%S')
        //}
        stage('Stage 1') {
            steps {
              echo "${BRANCH_NAME}"
                sh "chmod u+x ./test.sh; sh test.sh"
            }
        }
        stage('setting build properties') {
           steps {
               //sh "echo Branch name is env.BRANCH_NAME"
               echo "Branch name is ${BRANCH_NAME}"
               //sh "echo Build number is env.BUILD_NUMBER"
               echo "Build number is ${BUILD_NUMBER}"
               //sh "echo Build date is `date '+%Y%m%d%H%M%S'`"
               //DATE=sh(date '+%Y%m%d%H%M%S')
               //echo "Build date is ${DATE}"
               //shortCommit=sh(git rev-parse HEAD)
               //echo "Commit ID is ${COMMIT}"
               script {
                   shortCommit = sh(returnStdout: true, script: "git log -n 1 --pretty=format:'%H'").trim()
                   date_value = sh(script: "date", returnStdout: true).toString().trim()
               }
               echo "Commit ID is ${shortCommit}"
               echo "date_value is ${date_value}"
           }
        }
    }
}
