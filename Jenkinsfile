pipeline {
  agent {
    docker {
      image 'maven'
      args '3.5-jdk-8'
    }
    
  }
  stages {
    stage('greet') {
      steps {
        sh 'echo "hello"'
      }
    }
    stage('test') {
      steps {
        sh 'mvn test'
      }
    }
  }
}