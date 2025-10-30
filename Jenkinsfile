pipeline {
	agent any
	environment{
		dockerHome  = tool 'myDocker'
		mavenHome  = tool 'myMaven'
		PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"
	}
	stages {
		stage ('Build'){
			steps {
				sh 'mvn --version'
				sh 'docker version'
				echo "Build"
			}
		}
				stage ('Test'){
			steps {
				echo "Test"
			}
		}
				stage ('IT test'){
			steps {
				echo "It test"
			}
		}
	}
}