pipeline {
    agent any

stages{
  stage('Build') {
    steps{
      sh 'g++ -o working working.cpp'
    }
  }

  stage('Test') {
    steps{
       sh './working'
    }
  }

  stage('Deploy') {
    steps{
      echo 'DEPLOYMENT SUCCESSFUL'
    }
  }
}
post {
    failure {
        echo 'Pipeline Failed'
    }
  }
}

