#!/usr/bin/env groovy

pipeline {

    agent {
        docker {
            image 'node'
            args '-u root -p 3000:3000'
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
                echo 'Deploying...'
                sh 'npm start & sleep 1'
            }
        }
    }
}
