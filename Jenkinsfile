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
                    sh 'mvn clean compile'
                }
            }
        }
        stage ('test') {
            steps {
                withMaven(maven : 'Maven') {
                    sh 'mvn test'
                }
            }
        }
        stage (' Upload Package to Nexus') {
            steps {
                withMaven(maven : 'Maven') {
                    sh 'mvn package'
                }
            }
        }
    }
}
