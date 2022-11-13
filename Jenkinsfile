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
                    nexusArtifactUploader artifacts: [[artifactId: 'onlinebookstore', classifier: '', file: 'target/onlinebookstore.war', type: 'war']], credentialsId: 'nexus2', groupId: 'onlinebookstore', nexusUrl: 'localhost:8081/', nexusVersion: 'nexus2', protocol: 'http', repository: 'BookStore-release', version: '1.0.0'
                }
            }
        }
    }
}
