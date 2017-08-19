pipeline {
    agent none 
    stages {
        stage('testAndRun') {
            agent { docker 'maven:3.5-jdk-8' } 
            steps {
                  checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/vikramjakhr/KSS-Jenkins.git']]])

                sh 'mvn test'
		sh 'mvn package'
            }
        }
    }
}
