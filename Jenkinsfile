pipeline {
	//agent any
	agent { docker { image 'node:20.10'} }
	stages {
		stage ('Build'){
			steps {
				//sh 'mvn --version'
				sh 'node --version'
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