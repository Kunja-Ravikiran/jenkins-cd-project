pipeline {
    agent any

    stages {

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t jenkins-cd-image .'
            }
        }

        stage('Deploy Application') {
            steps {
                sh '''
                docker stop jenkins-cd-app || true
                docker rm jenkins-cd-app || true
                docker run -d -p 8081:80 --name jenkins-cd-app jenkins-cd-image
                '''
            }
        }
    }
}
