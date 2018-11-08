pipeline {

    environment {
        ARTIFACTORY_REPO = credentials('ARTIFACTORY_HOST')
        ARTIFACTORY_CRED = credentials('ARTIFACTORY_DOCKER')
    }
   
    agent { node { label 'slave' } }

    stages {
        stage('Build image') {
            steps {
                echo 'Building...'
                sh """
                   cd image
                   docker build --pull -t "mszumski:latest" .
                """
            }
        }
        stage('Push image') {
            steps {
                echo 'Docker login....'
                sh """
                   docker login -u $ARTIFACTORY_CRED_USR -p $ARTIFACTORY_CRED_PSW $ARTIFACTORY_REPO
                """
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}
