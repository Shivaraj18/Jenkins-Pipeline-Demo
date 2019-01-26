pipeline{
	agent any 
		stages{
			stage('One'){
				steps{
					echo 'Stage one is running...'
				}
			}
			stage('Two'){
				steps{
					input ('Do you want to continue..? Yes/Abourt')
				}
			}
			stage('Three'){
				when{
					not{
						branch 'master'
					}
				}
				steps{
					echo "Hello! Third Stage"
				}
			}
			stage('Four'){
				parallel{
					stage('Unit Test'){
						steps{
							echo "Running the unit test..."
						}
					}
					stage('Integration Test'){
						agent{
							docker{
								reuseNode false
								image "ubuntu"
							}
						}
						steps{
							echo "Running Integration Test..."
						}
					}
					
				}
			}
		}
	
}
