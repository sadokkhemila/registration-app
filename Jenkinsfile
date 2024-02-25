pipeline {
    agent any
    tools {
        maven 'maven'
    }
    environment {
    //DOCKERHUB_CREDENTIALS = credentials('github-login')
    //REMOTE_SERVER = 'your-remote-server-ip'
   //REMOTE_USER = 'your-remote-server-user' 	  	  
  }
    stages {
        stage('checkout from git') {
            steps {
               git branch: 'main', url: 'https://github.com/sadokkhemila/registration-app.git'
            }
        }
        stage('Build') {
            steps {
                
                sh 'mvn clean install '
                
            }
    }
}
