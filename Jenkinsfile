pipeline{
    agent none
    stages{
        stage('clean--feature-1'){
            agent{
                label "ubuntu"
            }
            steps{
                sh "mvn clean"
            }
        }
        stage('test--feature-1'){
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
        stage('package--feature-1'){
            agent {
                label "windows"
            }
            steps{
                powershell "mvn package"
            }
        }
    }
}
