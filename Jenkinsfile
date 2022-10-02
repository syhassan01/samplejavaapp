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
    stage('Docker Push') {
	   steps {
		sh 'docker login -u syhassan01 -p $DOCKER_HUB_PWD '
		sh 'docker push syhassan01/samplejavaapp:$BUILD_NUMBER'
           }
        }   	    
	    
	    
	    
        
    }
}
