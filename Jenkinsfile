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
                    deployToEnv("dev", 7001)
                }
            }
        }
        stage('tests-on-dev') {
            steps {
                script {
                    performTestsOoEnv("dev")
                }
            }
        }
        stage('deploy-to-staging') {
            steps {
                script {
                    deployToEnv("staging", 7002)
                }
            }
        }
        stage('tests-on-staging') {
            steps {
                script {
                    performTestsOoEnv("staging")
                }
            }
        }
        stage('deploy-to-preprod') {
            steps {
                script {
                    deployToEnv("preprod", 7003)
                }
            }
        }
        stage('tests-on-preprod') {
            steps {
                script {
                    performTestsOoEnv("preprod")
                }
            }
        }
        stage('deploy-to-prod') {
            steps {
                script {
                    deployToEnv("prod", 7004)
                }
            }
        }
        stage('tests-on-prod') {
            steps {
                script {
                    performTestsOoEnv("prod")
                }
            }
        }
    }
}


def build() {
    echo "Build started"
    clonePythonGreetingsRepo()

    echo "Installing required dependencies"
    bat "pip install -r requirements.txt"

    echo "Build finished"
}

def clonePythonGreetingsRepo() {
    cloneRepo("Python Greetings", "https://github.com/mtararujs/python-greetings", "main", "4e91144")
}

def cloneJsApiFramework() {
    cloneRepo("JS API Framework", "https://github.com/mtararujs/course-js-api-framework", "main")
}

def cloneRepo(String repoName, String url, String branch, String commit = null) {
    echo "Repository ${repoName} cloning started"

    git(
        url: url,
        branch: branch
    )

    if (commit != null) {
        bat "git checkout ${commit}"
    }

    echo "Listing cloned files"
    bat 'dir'
    echo "Repository ${repoName} cloning finished"
}

def deployToEnv(String env, Integer port) {
    echo "Deployment started to the ${env} environment"

    clonePythonGreetingsRepo()
    bat "pm2 delete greetings-app-${env} & EXIT /B 0"

    bat "pm2 start app.py --name greetings-app-${env} --port ${port}"
//    bat "pm2 start app.py --name greetings-app-${env}"

    echo "Deployment finished to the ${env} environment"
}

def performTestsOoEnv(String env) {
    echo "Test execution started on ${env} environment"

    cloneJsApiFramework()
    bat "npm install"
    bat "npm run greetings greetings_${env}"

    echo "Test execution finished on ${env} environment"
}