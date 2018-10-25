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
            parallel {
                stage('package on windows'){
                    agent {
                        label "windows"
                    }
                    steps {
                        powershell "mvn package"
                    }
                }
                stage('package on ubuntu'){
                    agent {
                        label "ubuntu"
                    }
                    steps {
                        sh "mvn package"
                    }
                }
            }
        }
    }
}
