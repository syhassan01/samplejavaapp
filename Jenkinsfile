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
    stage('Docker Build') {
	   steps {
                sh 'cd $WORKSPACE'
		sh 'docker build -f Dockerfile -t syhassan01/samplejavaapp:$BUILD_NUMBER .'
           }
        }   
    stage('Approval') {
	   steps {
		input "Deploy to Dev?"
           }
        }  	    
	    
    stage('Docker Push') {
	   steps {
		sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'   
		sh 'docker push syhassan01/samplejavaapp:$BUILD_NUMBER .'
           }
        }   	    
	    
	    
	    
        
    }
}
