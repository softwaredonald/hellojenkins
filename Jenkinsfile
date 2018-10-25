pipeline{
    agent none
    stages{
        stage('clean on feature 2'){
            agent{
                label "ubuntu"
            }
            steps{
                sh "mvn clean"
            }
        }
        stage('test on feature 2'){
            parallel {
                stage('Test on windows on feature 2'){
                    agent {
                        label "windows"
                    }
                    steps {
                        powershell "mvn test"
                    }
                }
                stage('Test on Linux on feature 2'){
                    agent{
                        label "ubuntu"
                    }
                    steps {
                        sh "mvn test"
                    }
                }
            }
        }
        stage('package on feature 2'){
            parallel {
                stage('package on windows on feature 2'){
                    agent {
                        label "windows"
                    }
                    steps {
                        powershell "mvn package"
                    }
                }
                stage('package on ubuntu on feature 2'){
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
