pipeline {
  agent any
  stages {
    stage('stage1') {
      steps {
        script {
          try {
            timeout(time: 20, unit: 'SECONDS') {
              input 'Do you want to proceed to the Deployment?'
            }
          } catch(err) {
            err.printStackTrace()
          }
          sh 'echo Proceeding'    
        }
      }
    }
    stage('stage2') {
      steps {
        script {
          checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/vikramjakhr/KSS-Jenkins.git']]])
        }
      }
    }
    stage('stage3') {
      agent { docker 'maven:3.5-jdk-8' }
      steps {
        script {
          sh 'mvn test'
        }
      }
    }
    stage('stage4') {
      agent { docker 'maven:3.5-jdk-8' }
      steps {
        script {
            sh 'mvn package'
        }
      }
    }
    stage('stage5') {
      steps {
        script {
          sh 'docker build -t maven:tag1'
        }
      }
    }      
  }
}

