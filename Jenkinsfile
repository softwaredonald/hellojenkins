pipeline {
    agent {label 'windows'}
    stages {
        stage('---clean---') {
            steps {
                powershell "mvn clean"
            }
        }
        stage('--test--') {
            steps {
                powershell "mvn test"
            }
        }
        stage('--package--') {
            steps {
                powershell "mvn package"
            }
        }
    }
}
