#!groovy

pipeline {

  agent any

  environment {
    git_commit_message = ''
    git_commit_diff = ''
    git_commit_author = ''
    git_commit_author_name = ''
    git_commit_author_email = ''
  }

  stages {

    // Build
    stage('Build') {
      agent {
        label 'master'
      }
      steps {
        //deleteDir()
        checkout scm
      }
    }

  stage('Deploy') {
            when {
              expression {
                currentBuild.result == null || currentBuild.result == 'SUCCESS' (1)
              }
            }
            steps {
                sh 'make publish'
            }
        }
  }
  post {
    success {
      sh "echo 'Send mail on success'"
       mail to:"sandeep.krs@hcl.com", subject:"SUCCESS: ${currentBuild.fullDisplayName}", body: "Yay, we passed."
    }
    failure {
      sh "echo 'Send mail on failure'"
       mail to:"sandeep.krs@hcl.com", subject:"FAILURE: ${currentBuild.fullDisplayName}", body: "Boo, we failed."
    }
  }
}
