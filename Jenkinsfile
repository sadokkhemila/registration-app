pipeline {
    agent any
    tools {
        maven 'maven'
    }
    environment {
        SCANNER_HOME = tool 'sonar-scanner'
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
                withSonarQubeEnv('sonar-scanner') {
                    sh ''' $SCANNER_HOME/bin/sonar-scanner -Dsonar.projectName=maven\
                    -Dsonar.projectKey=maven '''
                }
            }
        }
    }
}
