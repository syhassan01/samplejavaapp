pipeline {
    agent any
    tools { 
        maven 'maven3.8' 
        jdk 'java8' 
    }	    
    stages {
        stage('Checkout') {
	   steps {
                git branch: 'master', url: 'https://github.com/syhassan01/samplejavaapp.git'
           }
        }  
	 stage('Execute Maven') {
	   steps {
                sh 'mvn package'
           }
        }     
        
    }
}
