//Scripted
// node {
	
// 		echo "Build"

// 		echo "Test"

// 		echo "Test"
// 	}

// Declarative

pipeline {
	// agent any
	agent { docker {image 'maven:3.6.3'}}
	stages {
		stage('Build') {
			steps {
				sh "mvn --version"
				echo "Build"
			}
		}
		stage('Test') {
			steps {
				echo "Test"
			}
		}
		stage('Integration Test') {
			steps {
				echo "Integration Test"
			}
		} 
	} 
	post {
		always {
			echo 'I am awsome'
		}
		success {
			echo 'I run when you are successfully'
		}
		failure {
			echo 'I run when you fail'
		}
	}

}
