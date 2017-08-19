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
    stage('Docker Build') {
      agent any
      steps {
       withDockerRegistry([credentialsId: 'c0e73978-1098-4097-8a23-7fa2aa508313', url: "https://hub.docker.com/"]) {

               script {
       
             def image = docker.build("gaurav2090/kss:latest",'.')
             image.push()
               }}}}
    stage('artifact save') {
      steps {
        archiveArtifacts(allowEmptyArchive: true, artifacts: 'target/**/')
      }
    }
  }
}
