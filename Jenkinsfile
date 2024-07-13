// SCRIPTED

// DECLARATIVE

pipeline {
	agent any

	environment {
		dockerHome = tool 'myDocker'
		mavenHome = tool 'myMaven'
		PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"
	}

	stages {
		stage('Build') {
			steps {
				echo 'mvn --version'
				echo 'docker version'
			}
		}
		stage('Test') {
			steps {
				echo 'Test'
			}
		}
		stage('Integration Test') {
			steps {
				echo 'Integration Test'
			}
		}
	}
	post {
		always {
			echo 'I\'m awesome. I always run.'
		}
		success {
			echo 'Success.'
		}
		failure {
			echo 'Fail.'
		}
	}
}
