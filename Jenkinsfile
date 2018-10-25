pipeline {
    agent none
    stages {
        stage('---clean---') {
            agent {
                label'ubuntu'
            }
            steps {
                sh "mvn clean"
            }
        }
        stage('--test--') {
            parallel linux:{
                node('ubuntu1804'){
                    steps {
                        sh "mvn test"
                    }
                }           
            },
            windows:{
                node('windows'){
                    powershell "mvn test"
                }
            }
        }
        stage('--package--') {
            parallel linux:{
                node('ubuntu1804'){
                    steps {
                        sh "mvn package"
                    }
                }           
            },
            windows:{
                node('windows'){
                    powershell "mvn package"
                }
            }
        }
    }
}
