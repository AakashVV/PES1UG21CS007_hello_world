pipeline {
	agent any
	stages {
		stage('Clone repository') {
			steps {
				checkout([$class: 'GitSCM',
				branches: [[name: '*/main']],
				userRemoteConfigs: [[url: 'https://github.com/AakashVV/PES1UG21CS007_Jenkins.git']]])
			}
		}
		stage('Build') {
			steps {
				build 'PES1UG21CS007-1'
				sh 'g++ .\main.cpp -o output'
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
			}
		}
	}
	post {
		failure {
			echo 'Pipeline failed'
		}
	}
}
