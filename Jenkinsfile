pipeline {
    
    agent any 
    
    stages {
        stage('Git Checkout') {
            steps{
                script{
                    git branch: 'master', url: 'https://github.com/khadar099/automation-to-k8s.git'
                    }
                }
            }
        stage ('deploy docker image') {
            steps {
               sh '''
               ssh -o StrictHostKeyChecking=no -tt ubuntu@172.31.62.199
               mkdir bashad
               cd bashad
               touch khadar
               EOF
               exit
               sh '''
            
        }
    }
}
}
