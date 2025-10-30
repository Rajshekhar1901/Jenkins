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
				echo "PATH - $PATH"
				echo "BUILD_NUMBER - $env.BUILD_NUMBER"
				echo "BUILD_ID - $env.BUILD_ID"
				echo "JOB_NAME - $env.JOB_NAME"
				echo "BUILD_TAG - $env.BUILD_TAG"
				echo "BUILD_URL - $env.BUILD_URL"
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
		stage ('It Test'){
			steps {
				sh "mvn failsafe:integration-test failsafe:verify"
			}
		}
		stage ('package'){
			steps {
				sh "mvn package -DskipTests"
			}
		}
		stage ('Build Docker Image'){
			steps{
				//"docker biild -t rajshekharkg/docker_connection:$env.BUILD_TAG"
				script {
					dockerImage = docker.Build("rajshekharkg/docker_connection:${env.BUILD_TAG}")
				}
			}

		}
		stage ('push Docker Image'){
			steps{
				script {
					docker.withRegistry('', 'jenkins') {
					dockerImage.push();
					dockerImage.push('latest')
					}
				}
			}
		}
	} 
}