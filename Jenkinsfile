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
                echo "Building Application..."
                sh "sleep 5"
            }
        }

        stage('Quality Checks') {

            parallel {

                stage('Unit Test') {
                    steps {
                        echo "Running Unit Tests..."
                        sh "sleep 20"
                    }
                }

                stage('SonarQube') {
                    steps {
                        echo "Running Sonar Scan..."
                        sh "sleep 25"
                    }
                }

                stage('Trivy Scan') {
                    steps {
                        echo "Running Trivy Scan..."
                        sh "sleep 30"
                    }
                }

            }

        }

        stage('Docker Build') {
            steps {
                echo "Building Docker Image"
                sh "sleep 5"
            }
        }

        stage('Deploy') {
            steps {
                echo "Deploying to Kubernetes"
            }
        }

    }

}
