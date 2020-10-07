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
               script {
                   BUILD_COMMIT = sh(returnStdout: true, script: "git log -n 1 --pretty=format:'%H'").trim()
                   BUILD_DATE = sh(script: "date '+%Y%m%d%H%M%S'", returnStdout: true).toString().trim()
                   BUILD_BRANCH = sh(script: "echo ${env.JOB_NAME} | cut -d/ -f2", returnStdout: true).toString().trim()
                   //echo "Commit ID is ${BUILD_COMMIT}"
                   //echo "date is ${BUILD_DATE}"
                   //echo "branch is ${BUILD_BRANCH}"
                   //echo "Build number is ${BUILD_NUMBER}"
                   sh "sed -i 's/@BUILDNUMBER@/${BUILD_NUMBER}/g' properties.json"
                   sh "sed -i 's/@BUILDCOMMIT@/${BUILD_COMMIT}/g' properties.json"
                   sh "sed -i 's/@BUILDBRANCH@/${BUILD_BRANCH}/g' properties.json"
                   sh "sed -i 's/@BUILDDATE@/${BUILD_DATE}/g' properties.json"
                   sh "cat properties.json"
               }
           }
        }
    }
}
