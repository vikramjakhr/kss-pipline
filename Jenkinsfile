pipeline {
  agent any
  stages {
    stage('testAndRun') {
      steps {
        checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/vikramjakhr/KSS-Jenkins.git']]])
        mvn test
        mvn package
      }
    }
  }
}
