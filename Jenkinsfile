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
                   build_commit = sh(returnStdout: true, script: "git log -n 1 --pretty=format:'%H'").trim()
                   build_date = sh(script: "date '+%Y%m%d%H%M%S'", returnStdout: true).toString().trim()
                   build_branch = sh(script: "echo ${env.JOB_NAME} | cut -d/ -f2", returnStdout: true).toString().trim()
                   echo "Commit ID is ${build_commit}"
                   echo "date is ${build_date}"
                   echo "branch is ${build_branch}"
                   echo "Build number is ${BUILD_NUMBER}"
               sh '''
               sed -i "s/@BUILDNUMBER@/${BUILD_NUMBER}/g" properties.json
               sed -i "s/@BUILDDATE@/${build_date}/g" properties.json
               sed -i "s/@BUILDBRANCH@/${build_branch}/g" properties.json
               sed -i "s/@BUILDCOMMIT@/${build_commit}/g" properties.json
               cat properties.json
               '''
               }
           }
        }
    }
}
