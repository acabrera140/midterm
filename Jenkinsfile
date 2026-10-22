pipeline {
	agent any

	stages {
		stage('Checkout') {
		steps {
		echo 'Checking out Spring Boot project'
		checkout scm
		}
	}

	stage('Build') {
		steps {
		echo 'Building Spring Boot JAR'
		sh 'chmod +x mvnw'
		sh './mvnw clean package'
		}
	}

	stage('Verify JAR') {
		steps {
		echo 'Verifying generated JAR'
		sh 'ls -lh target/*.jar'
		}
	}
}

post {
	success {
		archiveArtifacts artifacts: 'target/*.jar',
				fingerprint: true
		echo 'Pipeline completed successfully!'
		}
		failure {
			echo 'Pipeline failed.'
		}
	}
}

