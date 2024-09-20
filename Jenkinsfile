//Scripted
// node {
	
// 		echo "Build"

// 		echo "Test"

// 		echo "Test"
// 	}

// Declarative

pipeline (
	agent any
	stages {
		stage('Build') {
			steps {
				echo "Build"
				
				echo "build"
			}
		}
		stage('Test') {
			step {
				echo "Test"
			}
		}
		stage('Integration Test') {
			step {
				echo "Integration Test"
			}
		} 
	}

)
