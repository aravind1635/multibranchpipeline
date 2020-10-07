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
               //echo "Branch name is ${BRANCH_NAME}"
               echo "Build number is ${BUILD_NUMBER}"
               script {
                   shortCommit = sh(returnStdout: true, script: "git log -n 1 --pretty=format:'%H'").trim()
                   date_value = sh(script: "date '+%Y%m%d%H%M%S'", returnStdout: true).toString().trim()
                   branch = sh(script: "echo ${env.JOB_NAME} | cut -d/ -f2", returnStdout: true).toString().trim()
                   echo "Commit ID is ${shortCommit}"
                   echo "date is ${date_value}"
                   echo "branch is ${branch}"
               }
           }
        }
    }
}
