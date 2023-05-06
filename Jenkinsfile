//Scripted
// node {
// 	stage('Build') {
// 		echo "Build"
// 	}
// 	stage('Test') {
// 		echo "Test"
// 	}
// 	stage('Integration Test') {
// 		echo "Integration Test"
// 	}
// 	stage('Regression Test') {
// 		echo "Regression Test"
// 	}
// }


//Declarative
pipeline {
	agent any
	stages {
		stage('Build') {
			steps {
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
			echo "I am awesome, I execute always"
		}
		success {
			echo "I execute when you are successful"
		}
		failure {
			echo "I execute when you fail"
		}
	}
}