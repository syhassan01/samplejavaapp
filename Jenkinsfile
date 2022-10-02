pipeline {
    agent {
        label 'Docker_hassan'
    }
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
      	        withCredentials([usernamePassword(credentialsId: 'dockerHub', passwordVariable: 'dockerHubPassword', usernameVariable: 'dockerHubUser')]) {
        	sh "docker login -u ${env.dockerHubUser} -p ${env.dockerHubPassword}"
          sh 'docker push syhassan01/samplejavaapp:$BUILD_NUMBER'
        }
      }
    }
    stage('DEV') {
	   steps {
		echo "HASSAN"
           }
           post {
                unstable {
                    echo "The current build $BUILD_NUMBER is unstable"
                }
		aborted  {
                    echo "The current build $BUILD_NUMBER is aborted."
                }
		failure  {
                    echo "The current build $BUILD_NUMBER is failed."
                }
		success {
                    echo "The current build $BUILD_NUMBER is succeeded."
                }  
            } 		   
	} 	   
    stage('UAT') {
	   steps {
		echo "HASSAN"
           }
           post {
                unstable {
                    echo "The current build $BUILD_NUMBER is unstable"
                }
		aborted  {
                    echo "The current build $BUILD_NUMBER is aborted."
                }
		failure  {
                    echo "The current build $BUILD_NUMBER is failed."
                }
		success {
                    echo "The current build $BUILD_NUMBER is succeeded."
                }  
            } 		   
	} 			   
    stage('PROD') {
	   steps {
		echo "HASSAN"
           }
           post {
                unstable {
                    echo "The current build $BUILD_NUMBER is unstable"
                }
		aborted  {
                    echo "The current build $BUILD_NUMBER is aborted."
                }
		failure  {
                    echo "The current build $BUILD_NUMBER is failed."
                }
		success {
                    echo "The current build $BUILD_NUMBER is succeeded."
                }  
            } 		   
	} 	

           
    }
}
