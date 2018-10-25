pipeline{
    agent none
    stages{
        stage('clean on feature 1'){
            agent{
                label "ubuntu"
            }
            steps{
                sh "mvn clean"
            }
        }
        stage('test on feature 1'){
            parallel {
                stage('Test on windows on feature 1'){
                    agent {
                        label "windows"
                    }
                    steps {
                        powershell "mvn test"
                    }
                }
                stage('Test on Linux on feature 1'){
                    agent{
                        label "ubuntu"
                    }
                    steps {
                        sh "mvn test"
                    }
                }
            }
        }
        stage('package on feature 1'){
            parallel {
                stage('package on windows on feature 1'){
                    agent {
                        label "windows"
                    }
                    steps {
                        powershell "mvn package"
                    }
                }
                stage('package on ubuntu on feature 1'){
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
