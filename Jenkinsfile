pipeline {
    agent {
        docker {
            image 'node:20-alpine'
        }
    }
    environment {
        FIREBASE_DEPLOY_TOKEN = credentials('FIREBASE_DEPLOY_TOKEN')
    }
    stages {
        stage('Build') {
            steps {
                sh 'npm install -g firebase-tools'
            }
        }
        stage('Testing') {
            steps {
                sh 'firebase deploy -P testing --token $FIREBASE_DEPLOY_TOKEN'
            }
        }
        stage('Staging') {
            steps {
                sh 'firebase deploy -P staging --token $FIREBASE_DEPLOY_TOKEN'
            }
        }
        stage('Production') {
            steps {
                sh 'firebase deploy -P production --token $FIREBASE_DEPLOY_TOKEN'
            }
        }
    }
}