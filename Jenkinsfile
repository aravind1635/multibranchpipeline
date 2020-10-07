pipeline {
    agent any 
    stages {
        stage('Stage 1') {
            steps {
              echo "${BRANCH_NAME}"
                sh "chmod u+x ./test.sh; sh test.sh"
            }
        }
        stage('setting build properties') {
           steps {
               //sh "echo Branch name is env.BRANCH_NAME"
               echo "Branch name is env.BRANCH_NAME"
               //sh "echo Build number is env.BUILD_NUMBER"
               echo "Build number is env.BUILD_NUMBER"
               //sh "echo Build date is `date '+%Y%m%d%H%M%S'`"
               echo "Build date is `date '+%Y%m%d%H%M%S'`"
               //shortCommit = sh(returnStdout: true, script: "git log -n 1 --pretty=format:'%h'").trim()
               echo "Commit ID is ${shortCommit}"
           }
        }
    }
}
