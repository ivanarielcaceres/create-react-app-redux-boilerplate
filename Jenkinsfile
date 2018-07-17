#!/usr/bin/env groovy

pipeline {

    agent {
        docker {
            image 'node'
            args '-u root -p 3000:3000'
        }
    }
    
    environment {
        CI = 'true'
    }

    stages {
        stage('Build') {
            steps {
                echo 'Building...'
                sh 'npm install'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing...'
                sh 'npm test -- --coverage --no-cache'
            }
        }
        stage('Deliver') {
            steps {
                sh 'npm run build'
                sh 'npm start & sleep 1'
                sh 'echo $! > .pidfile'
            }
        }
    }
}
