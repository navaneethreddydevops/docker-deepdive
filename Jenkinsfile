@Library('jenkins-shared-library@master') _

pipeline {
    agent none
    stages {
        stage ('Checkout') {
            steps {
                // log.info 'Starting' 
                script { 
                    log.info 'Checking Our'
                    log.warning 'Checkout is going on!'
                }
            }
        }
        stage ('Build') {
            steps {
                // log.info 'Starting' 
                script { 
                    log.info 'Building'
                    log.warning 'Build is going on!'
                }
            }
        }
        stage ('Deploy') {
            steps {
                // log.info 'Starting' 
                script { 
                    log.info 'Deploying'
                    log.warning 'Deploying is going on!'
                }
            }
        }
    }
}