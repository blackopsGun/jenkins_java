pipeline {
	agent any
	enviorment {
		DOCKER_IMAGE= 'hello-world:latest' //Docker image name
	}
	
	stages {
	  stage('checkout') {
		steps {
			checkout scm
		}
	}

	stage('Build') {
	   steps {
		sh 'javac HelloWorld.java'

		}
	}
	stage('Package') {
	steps {
		sh 'jar cf HelloWorld.jar HelloWorld.class'

		}

	}
	stage('Docker Build')
	steps {
		sh """
		docker build -t $DOCKER_IMAGE .
		"""
		}
	}
}
}

	post {
		success {
			  echo 'build completed successfully.'
		}
		failure {
				echo 'build failed'
		}
	}
}
