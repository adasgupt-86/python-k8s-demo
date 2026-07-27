pipeline {

    agent any

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Branch Info') {
            steps {
                echo "Branch Name : ${env.BRANCH_NAME}"
            }
        }

        stage('Build') {
            steps {
                sh 'echo Building DEVELOP Branch'
            }
        }

        stage('Test') {
            steps {
                sh 'echo Running Tests'
            }
        }

        stage('Done') {
            steps {
                echo 'Pipeline Finished'
            }
        }
    }
}
