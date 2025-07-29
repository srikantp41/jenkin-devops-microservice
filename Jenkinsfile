pipeline {
	agent any
	//agent { docker { image 'maven:3.6.3' } }
	environment {
		mavenHome = tool 'myMaven'
		dockerHome = tool 'myDocker'
		PATH = "$mavenHome/bin:$dockerHome/bin:$PATH"
	}
	stages {
		stage("Build") {
			steps {
				sh 'mvn --version'
				sh 'docker version'
				echo "Build"
				echo "DOCKET_HOME - $dockerHome"
				echo "PATH - $PATH"
				echo "BUILD_NUMBER - $BUILD_NUMBER"
				echo "BUILD_ID - $BUILD_ID"
				echo "BUILD_TAG - $BUILD_TAG"
				echo "JOB_NAME - $JOB_NAME"
			}
		}
		stage("Test") {
			steps {
				echo "Test"
			}
		}
		stage("Integration Test") {
			steps {
				echo "Integration Test"
			}
		}

	}
	post {
		always {
			echo "i am awesome, i run always"
		}
		success {
			echo "i run whe you are successful"
		}
		failure {
			echo "i run when you fail"
		}
		// unstable, changed steps
	}
}