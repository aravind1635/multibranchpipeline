pipeline {
    agent any 
    stages {
        stage('Stage 1') {
            steps {
              echo "${BRANCH_NAME}"
                sh "chmod u+x ./test.sh; sh test.sh ${GIT_USER_TO_CLONE} ${GIT_PASSWORD_TO_CLONE}"
            }
        }
    }
}
