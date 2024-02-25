pipeline {
    agent any
    tools {
        maven 'maven'
    }
   
    stages {
        stage('checkout from git') {
            steps {
               git branch: 'main', url: 'https://github.com/sadokkhemila/registration-app.git'
            }
        }
        stage('Build') {
            steps {
                dir ('webapp') {
                sh 'mvn package '
                }                 
            }
        }
    }
}
