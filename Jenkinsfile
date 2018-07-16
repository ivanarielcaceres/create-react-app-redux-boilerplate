#!/usr/bin/env groovy

pipeline {

    agent {
        docker {
            image 'node'
            args '-u root'
        }
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