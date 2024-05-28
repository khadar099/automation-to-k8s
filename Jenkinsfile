pipeline {
    
    agent any 
    
    stages {
        stage('Git Checkout'){
            steps{
                script{
                    git branch: 'master', url: 'https://github.com/khadar099/automation-to-k8s.git'
                    }
                }
            }
        stage('Maven build') {
            
            steps {
                
                script{
                    
                    sh 'mvn clean install'
                }
            }
        }
        stage ('Docker Build Stage') {
            steps {
                script {
                    sh 'docker image build -t $JOB_NAME:v1.$BUILD_ID .'
                    sh 'docker image tag $JOB_NAME:v1.$BUILD_ID khadar3099/$JOB_NAME:v1.$BUILD_ID'
                }
            }
        }
        stage ('push docker image to  dockerhub') {
            steps {
                script {
                   withCredentials([string(credentialsId: 'dockerpassword', variable: 'dockerpswrdtopush')]) {
                        sh 'docker login -u khadar3099 -p ${dockerpswrdtopush}'
                        sh 'docker image push khadar3099/$JOB_NAME:v1.$BUILD_ID'
                        //sh "docker rmi khadar3099/$JOB_NAME:v1.$BUILD_ID"
                        //sh 'docker run -d -p 9191:9090 khadar3099/$JOB_NAME:v1.$BUILD_ID'
                    }
                }
            }
        }
    }
}
