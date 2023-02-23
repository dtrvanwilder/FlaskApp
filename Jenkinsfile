pipeline {
    agent any
    
    stages {
        stage('Build') {
            steps {
                git url: 'https://github.com/dtrvanwilder/FlaskApp.git'
                sh 'docker build -t jtgluck/flaskapp .'
            }
        }
        stage('Publish') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'Docker', usernameVariable: 'jtgluck', passwordVariable: 'Boost_1234!')]) {
                    sh 'docker login -u $DOCKER_USERNAME -p $DOCKER_PASSWORD'
                    sh 'docker tag jtgluck/flaskapp jtgluck/flaskapp:latest'
                    sh 'docker push jtgluck/flaskapp:latest'
                }
            }
        }
    }
}
