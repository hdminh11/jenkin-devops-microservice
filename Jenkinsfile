// SCRIPTED

// DECLARATIVE

pipeline {
	agent any
	stages {
		stage('Build') {
			steps {
				echo 'Build'
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
