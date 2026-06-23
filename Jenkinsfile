pipeline {
    agent any

    environment {
        ACE_HOME = "C:\\Program Files\\IBM\\ACE\\13.0.7.0"
        ACE_BIN = "${ACE_HOME}\\server\\bin"
        NODE_HOST = "DESKTOP-K2EKDF6"
        NODE_PORT = "4414"
        INTEGRATION_SERVER = "EG1"
        BAR_NAME = "SampleAPI.bar"
    }

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Verify ACE Environment') {
            steps {
                bat """
                call "${ACE_BIN}\\mqsiprofile.cmd"
                where mqsideploy
                where mqsibar
                """
            }
        }

        stage('Build BAR') {
            steps {
                bat """
                call "${ACE_BIN}\\mqsiprofile.cmd"

                ibmint package ^
                  --input-path artifacts\\SampleAPI ^
                  --output-bar-file ${BAR_NAME}
                """
            }
        }

        stage('Deploy to EG1') {
            steps {
                bat """
                call "${ACE_BIN}\\mqsiprofile.cmd"

                mqsideploy ^
                  -i ${NODE_HOST} ^
                  -p ${NODE_PORT} ^
                  -e ${INTEGRATION_SERVER} ^
                  -a ${BAR_NAME}
                """
            }
        }

        stage('Verify Workspace') {
            steps {
                bat """
                dir
                dir artifacts
                """
            }
        }
    }

    post {
        success {
            echo '✅ CI/CD Pipeline SUCCESS - BAR deployed to EG1'
        }

        failure {
            echo '❌ Pipeline FAILED - check logs'
        }
    }
}
