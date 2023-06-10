pipeline {
    agent any
    tools{
        maven 'maven'
    }
    stages{
        stage('Build Maven'){
            steps{
                checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/jerald06/deocker-springboot.git']])
                bat 'mvn clean install'
            }
        }
        stage('Build docker image'){
            steps{
                   script {
                    bat 'docker build -t jero/spring-boot-docker .'
                    }

            }
        }
        stage('Docker run Container'){
     steps {
     script{
               bat 'docker run -p 9093:8080 jero/spring-boot-docker'
               }
     }
        }
    }
}