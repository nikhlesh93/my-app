

pipeline {
    agent any
    stages {
        stage('Clone') {
            steps {
                git 'https://github.com/nikhlesh93/my-app.git'
            }
        }
        stage('Build') {
            steps {
                script {
                    docker.build('my-app')
                }
            }
        }
        stage('Deploy') {
            steps {
                script {
                    docker.stop('my-app') || true
                    docker.run('-d -p 3000:3000 --name my-app my-app')
                }
            }
        }
    }
}

