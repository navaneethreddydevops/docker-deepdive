@Library('jenkins-shared-library@master') _

pipeline {
    agent none
    stages {
        stage ('Checkout') {
            steps {
                // log.info 'Starting' 
                script { 
                    sh 'terraform --version'
                }
            }
        }
        stage ('Build') {
            steps {
                // log.info 'Starting' 
                script { 
                    sh 'kubectl --version' 
                }
            }
        }
        stage ('Deploy') {
            steps {
                // log.info 'Starting' 
                script { 
                    sh 'Docker --version' 
                }
            }
        }
    }
}