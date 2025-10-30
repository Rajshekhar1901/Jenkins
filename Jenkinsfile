pipeline{
	agent any
	// agent { docker { image 'maven:3.6.3'} }
	// agent { docker { image 'node:13.8'} }
	environment {
		dockerHome = tool 'myDocker'
		mavenHome = tool 'myMaven'
		PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"	
		}
	Stages {
		stage ('Build'){
			steps{
				sh 'mvn -- version'
				sh 'docker version'
				echo "PATH - $PATH"
				echo "BUILD_NUMBER - $env.BUILD_NUMBER"
				echo "BUILD_ID - $env.BUILD_ID"
				echo "JOB_NAME - $env.JOB_NAME"
				echo "BULID_TAG - $env.BULID_TAG"
				echo "BUILD_URL - $env.BULID_URL"
			}
		}
		
	}

}