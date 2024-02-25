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
        stage('test sonarqube'){
            steps{
                withSonarQubeEnv('sonarqube') {
                    sh ''' $SCANNER_HOME/bin/sonar-scanner -Dsonar.projectName=maven\
                    -Dsonar.projectKey=maven '''
                }
            }
        }
    }
}
