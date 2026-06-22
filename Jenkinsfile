pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo 'Building App Connect project in UAT branch'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests in UAT environment - Build Version 2'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying to UAT environment'
            }
        }
    }
}
