pipeline {
    agent any
    environment { 
        CC = 'clang'
        APPLICATION = 'MyFirstEBSApp'
        REGION = 'us-east-1'
        ENVIRONMENT = 'Myfirstebsapp-env'
        PLATFORM = 'Python'
    }
    stages {
        stage('Get identity') {
            steps {
                sh 'aws sts get-caller-identity'
            }
        }
        stage('Intialize the application') {
            steps {
                sh 'eb init "${APPLICATION}" --platform "${PLATFORM}"  --region "${REGION}"'
            }
        }
        stage('select the environment') {
            steps {
                sh 'eb use "${ENVIRONMENT}"'
            }
        }
        stage('Deploy') {
            steps {
                sh 'eb deploy'
            }
        }
        stage('Test') {
            steps {
                sh 'eb health'
                sh 'eb status'
            }
        }
    }
}
