//Scripted
// node {
	
// 		echo "Build"

// 		echo "Test"

// 		echo "Test"
// 	}

// Declarative

pipeline {
	agent any
	// agent { docker {image 'node:13.8'}}
	environment {
		dockerHome = tool 'myDocker'
		mavenHome = tool 'myMaven'
		PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"
	}
	stages {
		stage('Checkout') {
			steps {
				sh "mvn --version"
				sh "docker --version"
				echo "Build"
			}
		}
		stage('Compile') {
			steps {
				sh "mvn clean compile"
			}
		}
		// stage('Test') {
		// 	steps {
		// 		sh "mvn test"
		// 	}
		// }
		stage('Integration Test') {
			steps {
				sh "mvn failsafe:integration-test failsafe:verify"
			}
		}
		stage('Package') {
			steps {
				sh "mvn package -DskipTests"
			}
		}
		stage('Build Docker Image') {
			steps {
				// docker build -t bilalmushtaq39/aks-test:$env.BUILD_TAG
				script {
					dockerImage = docker.build("bilalmushtaq39/aks-test:${env.BUILD_TAG}")
				}
			}
		}
		stage('Push Docker Image'){
			steps {
				// script {
				// 	docker.withRegistery('', 'dockerhub') {
				// 	dockerImage.push();
				// 	dockerImage.push('latest');
				// 	}
				// }
				withDockerRegistry([url: 'https://index.docker.io/v1/', credentialsId: 'dockerhub']) {
            sh "docker push ${dockerImage.id}"

			// docker tag ${dockerImage.id}:latest
            // docker push ${dockerImage.id}:latest
			}
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

