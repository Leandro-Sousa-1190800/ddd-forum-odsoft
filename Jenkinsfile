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
                sh 'npm install'
                sh 'npm run-script build'
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