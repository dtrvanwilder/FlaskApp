pipeline {
    agent any


    stages {
        stage ('Build') {
            steps {
                sh 'docker build -t jtgluck/flaskapp .'
            }
        }
        stage('Login and Push'){
            steps {
                script {
                    withDockerRegistry(credentialsId: 'Docker') {
                        docker.build('jtgluck/flaskapp').push('latest')
                    }     
                }
            }
        }
    }
}