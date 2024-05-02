pipeline {
    agent any

    stages {
        stage('install-pip-deps') {
            steps {
                script {
                    build()
                }
            }
        }
        stage('deploy-to-dev') {
            steps {
                script {
                    deployToEnv("DEV")
                }
            }
        }
        stage('tests-on-dev') {
            steps {
                script {
                    performTestsOoEnv("DEV")
                }
            }
        }
        stage('deploy-to-staging') {
            steps {
                script {
                    deployToEnv("STAGING")
                }
            }
        }
        stage('tests-on-staging') {
            steps {
                script {
                    performTestsOoEnv("STAGING")
                }
            }
        }
        stage('deploy-to-preprod') {
            script {
                deployToEnv("PREPROD")
            }
        }
        stage('tests-on-preprod') {
            steps {
                script {
                    performTestsOoEnv("PREPROD")
                }
            }
        }
        stage('deploy-to-prod') {
            script {
                deployToEnv("PROD")
            }
        }
        stage('tests-on-prod') {
            steps {
                script {
                    performTestsOoEnv("PROD")
                }
            }
        }
    }
}


def build() {
    echo 'Installing required dependencies'
}

def deployToEnv(String env) {
    echo 'Deploying to the ${env} environment'
}

def performTestsOoEnv(String env) {
    echo 'Performing tests on ${env} environment'
}