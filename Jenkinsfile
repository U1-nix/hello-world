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
            steps {
                script {
                    deployToEnv("PREPROD")
                }
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
            steps {
                script {
                    deployToEnv("PROD")
                }
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
    echo "Build started"
    cloneRepo("Python Greetings", "https://github.com/mtararujs/python-greetings", "main")
    echo "Build finished"
}

def cloneRepo(repoName, url, branch) {
    echo "Repository ${repoName} cloning started"

    git(
        url: url,
        branch: branch
    )

    echo "Listing cloned files"
    bat 'dir'
    echo "Repository ${repoName} cloning finished"
}

def deployToEnv(String env) {
    echo "Deployment started to the ${env} environment"
    echo "Deployment finished to the ${env} environment"
}

def performTestsOoEnv(String env) {
    echo "Test execution started on ${env} environment"
    echo "Test execution finished on ${env} environment"
}