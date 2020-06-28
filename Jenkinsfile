pipeline{
	agent {label 'ubuntu'}
	stages{
		stage("Pull Latest Image"){
			steps{
				sh "docker pull akbarchandani/selenium-docker-linux"
			}
		}
		stage("Start Grid"){
			steps{
				sh "docker-compose up -d hub chrome firefox"
			}
		}
		stage("Run Test"){
			steps{
				sh "docker-compose up search-module book-flight-module"
			}
		}
	}
	post{
		always{
			archiveArtifacts artifacts: 'output/**'
			sh "docker-compose down"			
		}
	}
}
