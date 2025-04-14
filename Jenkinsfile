pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main',
                    credentialsId: '02547b78-69fd-423a-9aac-698408798521',
                    url: 'https://github.com/baleMus1/kiidom.git'
            }
        }
        stage('Build Docker Image') {
            steps {
                script {
                    def image = docker.build("baleMus1/kiidom:${env.BUILD_NUMBER}")
                }
            }
        }
        stage('Run Command') {
            steps {
                sh 'ls -l'
            }
        }
    }
    post {
        always {
            echo 'Pipeline completed.'
        }
        success {
            echo 'Build succeeded!'
        }
        failure {
            echo 'Build failed.'
        }
    }
}
