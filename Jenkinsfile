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
                script{
                    bat 'docker build -t jeraldjr/spring-boot-docker .'
                }
            }
        }
        stage('Push image to Hub'){
            steps{
                script{
                   withCredentials([string(credentialsId: 'hubpassword', variable: 'password')]) {
                     bat 'docker login -u jeraldjr -p ${password}'
}

              bat 'docker push jeraldjr/spring-boot-docker'
                }



            }
        }
    }
}