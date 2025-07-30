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
                sh 'firebase deploy -P finalTesting --token $FIREBASE_DEPLOY_TOKEN'
            }
        }
        stage('Staging') {
            steps {
                sh 'firebase deploy -P finalStaging --token $FIREBASE_DEPLOY_TOKEN'
            }
        }
        stage('Production') {
            steps {
                sh 'firebase deploy -P finalProduction --token $FIREBASE_DEPLOY_TOKEN'
            }
        }
    }
}