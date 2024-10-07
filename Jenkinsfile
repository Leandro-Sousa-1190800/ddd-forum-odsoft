// Run cross OS commands
def xCommand(command) {
    if(isUnix()){
        sh command
    }else{
        bat command
    }
}

pipeline {
    agent any
    environment {
        GIT_REPO_URL    = 'https://github.com/Leandro-Sousa-1190800/ddd-forum-odsoft'
        GIT_REPO_BRANCH = 'master'
    }
    tools {
            nodejs 'NodeJS 22.9.0'
        }
    triggers {
        pollSCM('H/5 * * * *')
        }
    stages {
        stage('Pull Repository'){
            steps{
                git branch: "${GIT_REPO_BRANCH}",
                    url: "${GIT_REPO_URL}"
            }
        }
        stage('Install dependencies'){
            steps{
                echo 'Installing dependencies...'
                xCommand('npm install')
                xCommand('npm run-script build')
            }
        }
        stage('Clean'){
            steps{
                echo 'Cleaning it up...'
                maven clean
            }
        }
        stage('Build') {
            steps {
                echo 'Building..'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}