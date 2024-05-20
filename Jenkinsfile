pipeline {
    agent any
    stages {
        stage('Build Maven') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/khadar099/automation-to-k8s.git']]])
                sh 'mvn clean install'
            }
        }
    }
}
