pipeline {
	agent any
	stages {
		stage('Build') {
			steps {
				build 'PES1UG21CS007-1'
				sh 'g++ main.cpp -o output'
				echo 'Build Stage Successful'
			}
		}
		stage('Test') {
			steps {
				sh './output'
				echo 'Test Stage Successful'
			}
		}
		stage('Deploy') {
			steps {
				echo 'Deployment Successful'
				sh 'g++ error.cpp -o output'
			}
		}
	}
	post {
		failure {
			error 'Pipeline failed'
		}
	}
}
