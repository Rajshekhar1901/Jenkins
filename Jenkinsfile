pipeline {
	//agent any
	agent { docker { image 'node:13.1'} }
	stages {
		stage ('Build'){
			steps {
				sh 'mvn --version'
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