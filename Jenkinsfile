pipeline {
	//agent any
	agent { docker { image 'node:13.1'} }
	dns:
      - 8.8.8.8
      - 1.1.1.1
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