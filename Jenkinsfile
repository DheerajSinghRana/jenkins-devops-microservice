// scripted

// Declarative
pipeline {
	    agent any
		stages{
			stage('Build'){
				steps{
                    echo "Build"
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
		} post{
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


		