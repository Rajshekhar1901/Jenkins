pipeline {
	//agent any
	agent {docker { image 'maven:3.9.11'} }
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