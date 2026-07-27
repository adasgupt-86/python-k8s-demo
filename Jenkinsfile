@Library('shared-lib') _

pipeline {

    agent any

    parameters {

        string(
            name: 'IMAGE_TAG',
            defaultValue: 'v1',
            description: 'Docker image tag'
        )

        text(
            name: 'RELEASE_NOTES',
            defaultValue: 'Initial Release',
            description: 'Release Notes'
        )

        choice(
            name: 'ENVIRONMENT',
            choices: ['DEV', 'QA', 'PROD'],
            description: 'Deployment Environment'
        )

        booleanParam(
            name: 'DEPLOY',
            defaultValue: true,
            description: 'Deploy to Kubernetes'
        )
    }

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Print Parameters') {
            steps {

                echo "Image Tag      : ${params.IMAGE_TAG}"
                echo "Environment    : ${params.ENVIRONMENT}"
                echo "Deploy         : ${params.DEPLOY}"
                echo "Release Notes:"
                echo "${params.RELEASE_NOTES}"

            }
        }

        stage('Docker Build') {
            steps {
                dockerBuild("adasgupt86/python-k8s-demo:${params.IMAGE_TAG}")
            }
        }

        stage('Docker Push') {
            steps {
                dockerPush("adasgupt86/python-k8s-demo:${params.IMAGE_TAG}")
            }
        }

        stage('Deploy') {

            when {
                expression {
                    return params.DEPLOY
                }
            }

            steps {
                deployApp()
            }

        }

    }

}
