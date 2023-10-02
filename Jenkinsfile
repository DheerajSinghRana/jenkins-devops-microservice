// scripted

// Declarative
pipeline {
	    agent any
		// agent { docker { image 'maven:3.6.3'}}
		environment {
			dockerHome = tool "myDocker"
			mavenHome = tool "myMaven"
			PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"
		}
		stages{
			stage('Checkout'){
				steps{
					sh 'mvn --version'
					sh 'docker version'
                    echo "Build"
					echo "BUILD NUMBER - $env.BUILD_NUMBER"
					echo "$env.BUILD_ID"
					echo "$env.JOB_NAME"
					echo "$env.BUILD_TAG"
				}
			}
			stage('Build') {
				steps{
					sh "mvn clean compile"
				}
			}
			stage('Test'){
				steps{
                    echo "mvn test"
				}
			}
			stage('Integration Test'){
				steps{
                    echo "mvn failsafe:integration-test failsafe:verify"
				}
			}
			stage ('Package'){
				steps{
					sh "mvn package -DskipTests"
				}
			}
			stage('Build Docker Image') {
				steps{
                   // docker build -t 83497/currency-exchange-devops:$env.BUILD_TAG
				   script {
					dockerImage = docker.build("83497/currency-exchange-devops:${env.BUILD_TAG}")
				   }
				}
			}
			stage('Push Docker Image') {
				steps{
				    script {
						docker.withRegistry('', 'dockerhub') {
						dockerImage.push();
						dockerImage.push('latest');
						}
					}	
				}
			}
		} 
		
		post{
			always {
				echo "Iam awesome"
			}
		    success {
			echo "i run when you are successfull"
	    	}
            failure {
				echo "i run when you fail"
			}

		}
	}


		