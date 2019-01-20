pipeline {
  agent { label 'linux' }
  tools {
    maven 'M3'
  }
  stages {
    stage('checkout') {
      steps {
        git 'https://github.com/wangmeiji/CICD-JenkinsFile'
      }
    }
    stage('Build') {
      steps {
        sh 'mvn clean compile'
      }
    }
    stage('Test') {
      steps {
        sh 'mvn test'
        junit '**/target/surefire-reports/TEST-*.xml'
      }
    }
    stage('Package') {
      steps {
        sh 'mvn package'
      }
    }
  }
}
