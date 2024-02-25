pipeline {
    agent any
    tools {
        maven 'maven'
    }
    environment {
        SCANNER_HOME = tool 'sonarqube'
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
        stage('test sonarqube'){
            steps{
                withSonarQubeEnv('sonarqube') {
                    sh ''' $SCANNER_HOME/bin/sonarqube -Dsonar.projectName=maven\
                    -Dsonar.projectKey=maven '''
                }
            }
        }
    }
}
