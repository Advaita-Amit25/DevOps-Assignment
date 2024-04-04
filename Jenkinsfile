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

      
    }
}