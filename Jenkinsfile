pipeline {
	agent any
	tools {
		maven 'Maven 3.5.2'
	}
	options {
		timeout(time: 10, unit: 'MINUTES') 
	}
	stages {
		stage ('Checkout') {
			steps {
				git branch: 'master', url: 'https://github.com/rcroce/springboot-product.git'
			}
		}
		stage ('Compile') {
			steps {
				sh 'mvn clean compile'
			}
		}
	}
}
