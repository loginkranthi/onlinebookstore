pipeline {
    agent any
    stages {
        stage ('Checkout') {
            steps {
                git credentialsId: 'KKK', url: 'https://github.com/loginkranthi/onlinebookstore'
                }
            }
        stage ('compile') {
            steps {
                withMaven(maven : 'Maven') {
                    bat 'mvn clean compile'
                }
            }
        }
        stage ('test') {
            steps {
                withMaven(maven : 'Maven') {
                    bat 'mvn test'
                }
            }
        }
        stage (' Package') {
            steps {
                withMaven(maven : 'Maven') {
                    bat 'mvn package'
                }
            }
        }
    }
}
