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

       
 	stage('Push the container'){
            steps{
              withCredentials([usernamePassword(credentialsId: 'docker', passwordVariable: 		      	'DOCKER_PASSWORD', usernameVariable: 'DOCKER_USERNAME')]) {
                sh 'echo "$DOCKER_PASSWORD" | docker login -u $DOCKER_USERNAME --password-stdin'
                sh "docker push amitsaini25/spring:myApp"
              }
            }




        }
    }
}