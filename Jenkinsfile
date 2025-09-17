pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'docker build -t image3 .'
            }
        }
        stage ("Tag") {
            steps {
                sh 'docker tag image3 bharathdammalapati/myfirstrepo:movie'
            }
        }
         stage('push') {
            steps {
                script {
                   withDockerRegistry(credentialsId: 'dockerhub') {
                       sh 'docker push bharathdammalapati/myfirstrepo:movie'
                   }
                }
            }
        }
        
        stage ("Deploy") {
            steps {
                sh 'docker run -itd --name movie-app -p 3333:80 bharathdammalapati/myfirstrepo:movie'
            }
        }
    }
}
