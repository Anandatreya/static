pipeline{
    agent any
    stages {
    stage('Lint HTML') {
              steps {
                  sh 'tidy -q -e index.html'
              }
         }
    stage('Upload to AWS') {
              steps {
                  withAWS(region:'ap-southeast-1',credentials:'aws-static') {
                  sh 'echo "Uploading content with AWS creds"'
                      s3Upload(pathStyleAccessEnabled: true, payloadSigningEnabled: true, file:'index.html', bucket:'myjenkinbucket')
                  }
              }
         }
}
}