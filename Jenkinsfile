pipeline {
    agent any
    tools{
        maven 'maven'
    }
    stages{
        stage('Build Maven'){
            steps{
                checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/jerald06/deocker-springboot.git']])
                sh 'mvn clean install'
            }
        }
        stage('Build docker image'){
            steps{
                   script {
                    sh 'docker build -t jero/spring-boot-docker .'
                    }

            }
        }
        stage('Docker run Container'){
     steps {
     script{
               sh 'docker run -p 9093:8080 jero/spring-boot-docker'
               }
     }
        }
    }
}