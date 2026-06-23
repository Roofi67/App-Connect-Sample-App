pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Verify ACE') {
            steps {
                bat '''
                cd "C:\\Program Files\\IBM\\ACE\\13.0.7.0\\server\\bin"
                ibmint --help
                '''
            }
        }

        stage('Show Project') {
            steps {
                bat '''
                dir
                dir artifacts
                dir artifacts\\SampleAPI
                '''
            }
        }
    }
}
