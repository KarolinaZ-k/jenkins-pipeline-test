pipeline {
    agent dockerContainer { image 'maven:3.9.3-eclipse-temurin-17-alpine' }
    stages {
        stage('build') {
            steps {
                sh 'mvn --version'
            }
        }
        stage('Build') {
            steps {
                bat 'set'
            }
        }
        stage('Deploy') {
            steps {
                retry(3) {
                    sh './flakey-deploy.sh'
                }

                timeout(time: 3, unit: 'MINUTES') {
                    sh './health-check.sh'
                }
            }
        }
    }
}
