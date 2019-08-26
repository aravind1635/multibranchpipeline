pipeline {
    agent any 
    stages {
        stage('Stage 1') {
            steps {
              echo "${BRANCH_NAME}"
                sh "chmod u+x ./test.sh; sh test.sh ${GITHUB_USER_TO_CLONE} ${GITHUB_PASSWORD_TO_CLONE}"
            }
        }
    }
}
