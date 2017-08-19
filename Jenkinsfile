pipeline {
  agent {
    docker {
      image 'maven:3.5-jdk-8'
    }
    
  }
  stages {
    stage('test') {
      steps {
        parallel(
          "test": {
            sh 'mvn test'
            
          },
          "hello": {
            sh 'echo \'hello\''
            
          }
        )
      }
    }
    stage('build') {
      steps {
        sh 'mvn package'
      }
    }
    stage('deploy') {
      steps {
        sh 'ls'
      }
    }
  }
}