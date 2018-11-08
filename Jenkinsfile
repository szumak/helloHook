pipeline {

    environment {
        ARTIFACTORY_REPO = credentials('ARTIFACTORY_HOST')
        ARTIFACTORY_CRED = credentials('ARTIFACTORY_DOCKER')
        IMAGE_NAME       = "ARTIFACTORY_REPO/acme/" + "JOB_NAME".replaceAll('/', '_')
        IMAGE_NAME       = "IMAGE_NAME".toLowerCase()
    }
   
    agent { node { label 'slave' } }

    stages {
        stage('Build image') {
            steps {
                echo 'Building...'
                sh """
                   cd image
                   docker build --pull -t "${IMAGE_NAME}:latest" .
                """
            }
        }
        stage('Push image') {
            steps {
                echo 'Docker login....'
                sh """
                   docker login -u $ARTIFACTORY_CRED_USR -p $ARTIFACTORY_CRED_PSW $ARTIFACTORY_REPO
                   docker push "${IMAGE_NAME}:latest"
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
