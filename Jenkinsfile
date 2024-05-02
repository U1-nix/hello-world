pipeline {
    agent any

    stages {
        stage('install-pip-deps') {
            steps {
                echo 'Installing required dependencies'
            }
        }
        stage('deploy-to-dev') {
            steps {
                echo 'Deploying to the DEV environment'
            }
        }
        stage('tests-on-dev') {
            steps {
                echo 'Performing tests on DEV environment'
            }
        }
        stage('deploy-to-staging') {
            steps {
                echo 'Deploying to the STAGING environment'
            }
        }
        stage('tests-on-staging') {
            steps {
                echo 'Performing tests on STAGING environment'
            }
        }
        stage('deploy-to-preprod') {
            steps {
                echo 'Deploying to the PREPROD environment'
            }
        }
        stage('tests-on-preprod') {
            steps {
                echo 'Performing tests on PREPROD environment'
            }
        }
        stage('deploy-to-prod') {
            steps {
                echo 'Deploying to the PROD environment'
            }
        }
        stage('tests-on-prod') {
            steps {
                echo 'Performing tests on PROD environment'
            }
        }
    }
}