pipeline {
	agent any
	tools {
		maven 'Maven 3.5.2'
	}
	options {
        timeout(time: 10, unit: 'MINUTES') 
    }
	stages {
		stage ('Compile Stage') {
			steps {
				sh 'mvn clean compile'
			}
		}
	}
	post {
		always {
			deleteDir()
		}
    
		success {
			mail(to: "rodrigo.croce@gmail.com", 
				 subject: "SUCCESS: ${currentBuild.fullDisplayName}",
				 body: "Build passed!")
		}

		failure {
			mail(to: "rodrigo.croce@gmail.com", 
				 subject: "FAILURE: ${currentBuild.fullDisplayName}",
				 body: "Build failed!")
		}
	}
	
	options {
		buildDiscarder(logRotator(numToKeepStr:'10'))
		timeout(time: 30, unit: 'MINUTES')
	}
}
