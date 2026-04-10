pipeline {
    agent any
	
    environment {
	DOCKER_IMAGE = 'hello-world-python:latest'  
 
    }

    stages {
	stages('Checkout') {
	    steps {
		git branch: 'main', url:
		'https://github.com/Nikita1035/jenkins_file.git'
	     }

	}

	stage('Docker Build') {
	    
	    steps {
		script {
		    if (fieldExists('Dockerfile')) {
		    sh "docker build -t ${env.DOCKER_IMAGE} ."
		} else {
		    error "Dockerfile not found in the workspace. Please create one 
                    for your Python application."
		}
	   }
	}
    }
   
    stage('Docker Run (Optional)') {
	steps {
		sh "docker run --rm ${env.DOCKER_IMAGE}" 
    }}  }

    post {
	success { echo 'Success' }
	failure { echo 'Failure' }   }  }


