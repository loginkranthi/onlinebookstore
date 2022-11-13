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
        stage (' package ') {
            steps {
                withMaven(maven : 'Maven') {
                    sh 'mvn package'
                }
            }
        }
        stage ('Upload package to nexus') {
            steps {
                nexusArtifactUploader artifacts: [[artifactId: 'onlinebookstore-1.0.0', classifier: '', file: 'target/onlinebookstore.war', type: 'war']], credentialsId: 'nexus2', groupId: 'onlinebookstore', nexusUrl: 'localhost:8081/', nexusVersion: 'nexus2', protocol: 'http', repository: 'BookStore-release', version: '1.0.0'
                }
            }       
    }
}
