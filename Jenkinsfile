pipeline {
  agent {
    docker {
      image 'frankjmb/node-react-blue-app:latest'
      args '-p 3000:3000'
    }

  }
  stages {
    stage('Build') {
      steps {
      input 'npm install (Click "Proceed" to continue)'
      }
    }
    stage('Test') {
      environment {
        CI = 'true'
      }
      steps {
        sh './jenkins/scripts/test.sh'
      }
    }
    stage('Deliver') {
      steps {
        sh './jenkins/scripts/deliver.sh'
        input 'Finished using the web site? (Click "Proceed" to continue)'
        sh './jenkins/scripts/kill.sh'
      }
    }
  }
}
