pipeline {
  agent any 
  stages {
    stage('Build') {
      steps {
        sh 'tidy -e -q *.html'
      }
    }
    stage('Upload to AWS') {
      steps {
        withAWS(region:'us-west-2',credentials:'blueocean') {
          s3Upload(pathStyleAccessEnabled:true, payloadSigningEnabled: true, file:'index.html', bucket:'c3pipelines-rotimi')
        }
      }
    }
  }
}