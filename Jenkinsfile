pipeline {
  agent {
    docker {
      image'maven:3-alpine'
      args '-v /root/.m2:/root/.m2'
    }
  }

  stages {
    stage('Build') {
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
      steps {
        echo 'Deploying....'
      }
    }
  }
}
