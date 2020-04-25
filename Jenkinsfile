pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'echo "Hello World"'
      }
    }
    stage('Test') {
      steps {
        sh 'echo "Hello WorldAgain"'
      }
    }
    stage('Lint HTML') {
      steps {
        sh 'tidy -q -e *.html'
      }
    }
    stage('Upload to AWS') {
              steps {
                  withAWS(region:'eu-west-1',credentials:'AWSJenkins') {
                  sh 'echo "Uploading content with AWS creds"'
                      s3Upload(pathStyleAccessEnabled: true, payloadSigningEnabled: true, file:'index.html', bucket:'myjenkinscicdbucket')
                  }
         }
              }
    }
}
