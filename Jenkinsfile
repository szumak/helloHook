pipeline {
   
    agent { node { label 'slave' } }

    stages {
        stage('Build image') {
            steps {
                echo 'Building...'
                sh """
                   docker build --pull -t "mszumski:latest" image/Dockerfile
                """
            }
        }
        stage('Test') {
            steps {
                echo 'Testing....'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}
