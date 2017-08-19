pipeline {
  agent {
    docker {
      image 'maven:3.5-jdk-8'
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
    stage('build') {
      steps {
        sh 'mvn package'
      }
    }
    stage ('Docker Build') {
      steps{
        sh "docker build -t kss-docker ."
      }   
}
    stage('artifact save') {
      steps {
        archiveArtifacts(allowEmptyArchive: true, artifacts: 'target/**/')
      }
    }
  }
}
