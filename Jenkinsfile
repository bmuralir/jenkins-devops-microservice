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
	//agent { docker { image 'maven:3.6.3'}}
	environment {
		dockerHome = tool 'myDocker'
		mavenHome = tool 'myMaven'
		PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"
	}
	stages {
		stage('Checkout') {
			steps {
				sh 'mvn --version'
				sh 'docker version'
				echo "Build"
				echo "PATH - $PATH"
				echo "BUILD_NUMBER - $env.BUILD_NUMBER"
				echo "BUILD_ID - $env.BUILD_ID"
				echo "JOB_NAME - $env.JOB_NAME"
				echo "BUILD_TAG - $env.BUILD_TAG"
				echo "BUILD_URL - $env.BUILD_URL"

			}
		}
		stage('Compile') {
			steps{
				sh "mvn clean compile"
			}
		}

		stage('Test'){
			steps {
				sh "mvn test"
			}
		}
		stage('Integration Test'){
			steps {
				sh "mvn failsafe:integration-test failsafe:verify"
			}
		}
		// stage('Test') {
		// 	steps {
		// 		echo "Test"
		// 	}
		// }
		// stage('Integration Test') {
		// 	steps {
		// 		echo "Integration Test"
		// 	}
		// }
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
		changed {
			echo "executes when build status changes"
		}

	}
}