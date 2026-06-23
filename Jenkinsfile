pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build BAR') {
    steps {
        bat '''
        call "C:\\Program Files\\IBM\\ACE\\13.0.7.0\\server\\bin\\mqsiprofile.cmd"

        ibmint package ^
          --input-path artifacts/SampleAPI ^
          --output-bar-file SampleAPI.bar
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
