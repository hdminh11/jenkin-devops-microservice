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
				sh 'mvn --version'
				sh 'docker  version'
			}
		}
		stage('Compile') {
			steps {
				sh 'mvn clean compile'
			}
		}
		stage('Test') {
			steps {
				sh 'mvn test'
			}
		}
		stage('Integration Test') {
			steps {
				sh 'mvn failsafe:integration-test failsafe:verify'
			}
		}
		stage('Package') {
			steps {
				sh 'mvn package -DskipTests'
			}
		}
		stage('Build Docker image') {
			steps {
				// "docker build -t hoangducminh/currency-exchange-devops:$env.BUILD_TAG"
				script {
					dockerImage = docker.build("hoangducminh/currency-exchange-devops:${env.BUILD_TAG}")
				}
			}
		}
		stage('Push Docker image') {
			steps {
				script {
					docker.withRegistry('','dockerhub') {
						dockerImage.push();
						dockerImage.push('latest');
					}
				}
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
 