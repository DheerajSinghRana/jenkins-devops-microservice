// scripted

// Declarative
pipeline {
	    agent any
		// agent { docker { image 'maven:3.6.3'}}
		stages{
			stage('Build'){
				steps{
					// sh 'mvn --version'
                    echo "Build"
					echo "BUILD NUMBER - $env.BUILD_NUMBER"
					echo "$env.BUILD_ID"
					echo "$env.JOB_NAME"
					echo "$env.BUILD_TAG"
				}
			}
			stage('Test'){
				steps{
                    echo "Test"
				}
			}
			stage('Integration Test'){
				steps{
                    echo "Integration test"
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


		