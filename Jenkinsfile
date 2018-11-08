pipeline {

    environment {
        ARTIFACTORY_REPO = ARTIFACTORY_HOST
        ARTIFACTORY_USER = credentials('ARTIFACTORY_USER')
        ARTIFACTORY_PASS = credentials('ARTIFACTORY_PASS')
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
                docker login -u $ARTIFACTORY_USER -p $ARTIFACTORY_PASS $ARTIFACTORY_REPO
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}
