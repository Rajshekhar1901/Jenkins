pipeline {
	agent any
	environment{
		dockerHome  = tool 'myDocker'
		mavenHome  = tool 'myMaven'
		PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"
	}
	stages {
		stage ('Checkout'){
			steps {
				sh 'mvn --version'
				sh 'docker version'
				echo "Build"
			}
		}

		stage('Compile'){
			steps {
				sh "mvn clean compile"
			}
		}
		
		stage ('Test'){
			steps {
				sh "mvn test"
			}
		}

		stage ('IT test'){
			steps {
				echo "mvn failsafe:integration-test failsafe:verify"
			}
		}
	} 
}