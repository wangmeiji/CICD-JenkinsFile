pipeline {
  agent { label 'linux' }
  def mvn_version = 'M3'
  withEnv( ["PATH+MAVEN=${tool mvn_version}/bin"] ) {
  env.PATH = "${mvnHome}/bin:${env.PATH}"
  sh 'mvn -B verify'
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
