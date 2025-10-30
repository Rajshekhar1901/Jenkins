pipeline {
	agent any
	environment{
		dockerHome  = tool 'myDocker'
		mavenHome  = tool 'myMaven'
		// Keep tool paths available; don't force a PATH separator here so the pipeline works on both Windows and Unix agents.
		// Use `dockerHome` and `mavenHome` in steps instead of modifying PATH here.
	}
	stages {
		stage ('Checkout'){
			steps {
				script { 
					sh 'mvn --version'
					sh 'docker version'
					sh 'echo "Build"'
					sh 'echo "PATH - $PATH"'
					sh 'echo "BUILD_NUMBER - $BUILD_NUMBER"'
					sh 'echo "BUILD_ID - $BUILD_ID"'
					sh 'echo "JOB_NAME - $JOB_NAME"'
					sh 'echo "BUILD_TAG - $BUILD_TAG"'
					sh 'echo "BUILD_URL - $BUILD_URL"'
				}
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
				script {
					if (isUnix()) {
						sh 'mvn package -DskipTests'
					} else {
						bat 'mvn package -DskipTests'
					}
				}
			}
		}
		stage ('Build Docker Image'){
			steps{
				//"docker biild -t rajshekharkg/docker_connection:$env.BUILD_TAG"
				script {
					dockerImage = docker.build("rajshekharkg/docker_connection:${env.BUILD_TAG}")
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