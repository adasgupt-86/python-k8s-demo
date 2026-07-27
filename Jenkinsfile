@Library('shared-lib') _

pipeline {

    agent any

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Docker Build') {
            steps {
                dockerBuild("adasgupt86/python-k8s-demo:v1")
            }
        }

        stage('Docker Push') {
            steps {
                dockerPush("adasgupt86/python-k8s-demo:v1")
            }
        }

        stage('Deploy') {
            steps {
                deployApp()
            }
        }
    }
}
