pipeline {
  agent any

  stages {
    stage('Buzz Build') {
      steps {
        sh '''echo I am a $BUZZ_NAME
chmod +x jenkins/build.sh 
./jenkins/build.sh'''
        archiveArtifacts allowEmptyArchive: true, artifacts: 'target/*.jar', fingerprint: true, followSymlinks: false, onlyIfSuccessful: true
      }
    }

    stage('Buzz Test') {
      parallel {
        stage('Buzz Test') {
          steps {
            sh '''chmod +x jenkins/test-all.sh 
./jenkins/test-all.sh'''
            junit '**/surefire-reports/**/*.xml'
          }
        }

        stage('Testing B') {
          steps {
            sh '''sleep 10
echo done'''
          }
        }
      }
    }
  }

  environment {
    BUZZ_NAME = 'Worker Bee'
  }
}
