pipeline{
    agent none
    stages{
        stage('--clean--'){
            agent{
                label "ubuntu"
            }
            steps{
                sh "mvn clean"
            }
        }
        stage('--test--'){
            parallel {
                stage('Test on windows'){
                    agent {
                        label "windows"
                    }
                    steps {
                        powershell "mvn test"
                    }
                }
                stage('Test on Linux'){
                    agent{
                        label "ubuntu"
                    }
                    steps {
                        sh "mvn test"
                    }
                }
            }
        }
        stage('package'){
            agent {
                label "windows"
            }
            steps{
                powershell "mvn package"
            }
        }
    }
}
