pipeline {
    agent {
        docker {
            image 'node:14-alpine'
            args '-p 3000:3000'
        }
    }
    environment {
        CI = 'true' 
        HOME = '.'
    }
    stages {
        stage('Build') {
            steps {
                sh 'npm install'
            }
        }
        stage('Test') {
            steps {
                sh "chmod +x ./Test.sh"
                sh './Test.sh'
            }
        }
        stage('Deliver') {
            steps {
                sh "chmod +x ./deliver.sh"
                sh './deliver.sh'
                input message: 'Finished using the web site? (Click "Proceed" to continue)'                            
                }
            }
    }
}