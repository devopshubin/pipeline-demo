pipeline {
  agent any
  stages {
    stage('Buzz Build') {
      steps {
        sh '''echo I am a $BUZZ_NAME
chmod +x jenkins/build.sh 
./jenkins/build.sh'''
        archiveArtifacts(artifacts: 'target/*.jar', fingerprint: true)
      }
    }

    stage('Buzz Test') {
      steps {
        sh '''chmod +x jenkins/test-all.sh 
./jenkins/test-all.sh'''
        junit '**/surefire-reports/**/*.xml'
      }
    }

  }
  environment {
    BUZZ_NAME = 'Worker Bee'
  }
}