pipeline {
    agent any

    stages {

        stage('Code checkout according to environment') {
            steps {
                script{
                  checkout changelog: false, poll: false, scm: scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'gtihub-credentials', url: 'https://github.com/Advaita-Amit25/DevOps-Assignment.git']])
                }
            }
        }

        stage("Build the code") {
            steps {
                dir('DevOpsDemo') {
                    sh "chmod +x ./mvnw"
                    sh "./mvnw clean package"
                }
            }
        }

        stage('Create image for Docker') {
            steps {
                dir('DevOpsDemo') {
                    sh 'docker build -t spring:myApp .'
                }
            }
        }

        stage('Run the container') {
            steps {
                dir('DevOpsDemo') {
                    sh 'docker run -p 5500:8090 spring:myApp'
                }
            }
        }
    }
}