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
        echo PATH=%PATH%
        where ibmint
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
