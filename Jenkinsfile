pipeline {
  agent none
  stages {
    stage('testAndRun') {
      agent { docker 'maven:3.5-jdk-8' }
      steps {
        script {
          try {
            timeout(time: 20, unit: 'SECONDS') {
              input 'Do you want to proceed to the Deployment?'
            }
            checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/vikramjakhr/KSS-Jenkins.git']]])
            sh 'mvn test'
            sh 'mvn package'
            sh 'docker build -t maven:tag1 .'
          } catch(err) {
            err.printStackTrace()
          }
          sh 'echo Proceeding'    
        }
      }
    }      
  }
}

