pipeline {
	agent any
	//agent { docker { image 'maven:3.6.3' } }
	tools {
      jdk 'jdk-8'  // Must match name in Jenkins Global Tool Configuration
    }
	environment {
		//mavenHome = tool 'myMaven'
		//dockerHome = tool 'myDocker'
		mavenHome = "${tool 'myMaven'}"
		dockerHome = "${tool 'myDocker'}"
		JAVA_HOME = "${tool 'jdk-8'}"
		PATH = "${mavenHome}/bin:${dockerHome}/bin:/bin:$PATH"
	}
	stages {
		stage("Checkout") {
			steps {
				sh 'mvn --version'
				sh 'docker version'
				sh 'java -version'
				echo "Build"
				//echo "JAVA_HOME - ${env.JAVA_HOME}"
				echo "JAVA_HOME in Groovy: ${env.JAVA_HOME}"
                sh 'echo "JAVA_HOME in shell: $JAVA_HOME"'
				echo "DOCKET_HOME - ${dockerHome}"
				echo "PATH - $PATH"
				echo "BUILD_NUMBER - $BUILD_NUMBER"
				echo "BUILD_ID - $BUILD_ID"
				echo "BUILD_TAG - $BUILD_TAG"
				echo "JOB_NAME - $JOB_NAME"
			}
		}
		stage("Build") {
			steps {
				sh "mvn clean compile"
			}
		}
		stage("Test") {
			steps {
				sh "mvn test"
			}
		}
		stage("Integration Test") {
			steps {
			sh "mvn failsafe:integration-test failsafe:verify"
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