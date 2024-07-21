pipeline {
	agent any
	stages {
		stage('Checkout SCM') {
			steps {
				 git url: 'https://github.com/JasonICTSE/simple-node-js-react-npm-app.git'
			}
		}

		stage('OWASP DependencyCheck') {
			steps {
				dependencyCheck additionalArguments: '--format HTML --format XML', odcInstallation: 'OWASP_Dependency-Check_Vulnerabilities/dependency-check'
			}
		}
	}	
	post {
		success {
			dependencyCheckPublisher pattern: 'dependency-check-report.xml'
		}
	}
}