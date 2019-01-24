pipeline {
  agent {
     docker {
         image 'maven:3-alpine' 
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
      steps {
        echo 'Testing..'
	sh 'mvn test'
      }
    }
    stage('Deploy') {
      steps {
        echo 'Deploying....'
      }
    }
  }
  post {
    failure {
      mail to: 'chenjie@richinfo.cn',
      subject: "Failed Pipeline: ${currentBuild.fullDisplayName}",
      body: "Something is wrong with ${env.BUILD_URL}"
    }
    success {
      mail to: 'chenjie@richinfo.cn',
      subject: "Build Pipline success",
      body: "demo应用构建成功"
    }
  }
}
