pipeline {
    agent any 
    stages {
        stage('Stage 1') {
            steps {
              echo "${BRANCH_NAME}"
              echo "${GITHUB_USER_TO_CLONE}"
              echo "${GITHUB_PASSWORD_TO_CLONE}"
            }
        }
    }
}
