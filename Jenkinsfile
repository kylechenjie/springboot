pipeline {
  agent none

  stages {
    stage('Build') {
      agent {
        docker 'maven:3-alpine'
        args '-v /root/.m2:/root/.m2'
      }
      steps {
        echo 'Building..'
        sh 'mvn -B -DskipTests clean package'
      }
    }
    stage('Test') {
      agent {
        docker 'openjdk:8-jre'
      }
      steps {
        echo 'Testing..'
	      sh 'mvn test'
        sh 'java -version'
      }
    }
    stage('Deploy') {
      agent {
        docker 'openjdk:8-jre'
      }
      steps {
        echo 'Deploying....'
      }
    }
  }
}
