pipeline {
    agent any 
    stages {
        stage('Stage 1') {
            steps {
              echo "${BRANCH_NAME}"
                sh "chmod u+x ./test.sh; sh test.sh"
            }
        }
    }
}
