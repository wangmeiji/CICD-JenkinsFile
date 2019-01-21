pipeline {
  agent { label 'linux' }
  stages {
    stage('checkout') {
      steps {
        git 'https://github.com/wangmeiji/CICD-JenkinsFile'
      }
    }
    stage('Build') {
      def mvn_version = 'M3'
      withEnv( ["PATH+MAVEN=${tool mvn_version}/bin"] ) {
        env.PATH = "${mvnHome}/bin:${env.PATH}"
        sh 'mvn -B verify'
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
