pipeline {
    agent any
    stages {
        stage('HTML Lint') {
            steps {
                sh 'tidy -q -e *.html'
            }
        }
        stage('Upload to AWS') {
              steps {
                 withAWS(region:'us-east-2',credentials:'aws-static') {
                  sh 'echo "Uploading content with AWS creds"'
                      s3Upload(pathStyleAccessEnabled: true, payloadSigningEnabled: true, file:'index.html', bucket:'jenkins-s3-pipeline-udacity')
                 }
             }
         }
    }
}
