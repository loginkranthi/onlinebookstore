pipeline {
    agant any
    
    stages {
        stage ('compile stage') {
            steps {
                withMaven(maven : 'Maven') {
                    sh 'mvn clean compile'
                }
            }
        }
        stage ('testing Stage') {
            steps {
                withMaven(maven : 'Maven') {
                    sh 'mvn test'
                }
            }
        }
        stage (' Packaging stage ') {
            steps {
                withMaven(maven : 'Maven') {
                    sh 'mvn package'
                }
            }
        }
    }
}
