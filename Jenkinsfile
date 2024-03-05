pipeline {
	agent any
	stages {
		stage('Clone repository') {
			steps {
				checkout([$class: 'GitSCM',
				branches: [[name: '*/main']],
				userRemoteConfigs: [[url: 'https://github.com/AakashVV/PES1UG21CS007_Jenkins.git']]]
			}
		}
		stage('Build') {
			steps {
				build 'PES1UG21CS007-1'
				sh 'mvn clean install'
				sh 'g++ main.cpp -o output'
				echo 'Build Stage Successful'
			}
		}
		stage('Test') {
			steps {
				sh 'mvn test'
				sh './output'
				echo 'Test Stage Successful'
				post {
					always {
						junit 'target/surefire-reports/*.xml'
					}
				}
			}
		}
		stage('Deploy') {
			steps {
				sh 'mvn deploy'
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
