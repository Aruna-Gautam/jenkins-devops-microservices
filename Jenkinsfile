// node {
// 	stage('Build') {
// 		echo "Build"
// 	}
// 	stage('Test') {
// 		echo "Test"
// 	}
// }

pipeline 
{
	agent any
	environment{
		mavenHome = tool 'myMaven'
		dockerHome = tool 'myDocker'
		PATH = "$mavenHome/bin:$dockerHome/bin:$PATH"
	}
	//agent{docker{image 'maven:3.6.3'} }
	//agent{docker{image 'node:12.18.3'} }
	stages 
	{
		stage('Build')
		{
			steps {
				sh 'mvn --version'
				sh 'docker version' 
				echo "Build"
				echo "$PATH"
				echo "BUILD_NUMBER - $env.BUILD_NUMBER"
				echo "BUILD_ID - $env.BUILD_ID"
				echo "BUILD_TAG - $env.BUILD_TAG"
				echo "JOB_NAME - $env.JOB_NAME"
			}			
		}
		stage('Test')
		{
			steps {
			echo "Test"
			}
		}
		stage('IT')
		{
			steps {
			echo "Intergration test"
		} 
		}
	}			
		
post {
	always{
		echo "I am awesome, I run always"
	}
	success{
		echo "I run when you are successful"
	}
	failure{
		echo "I run when you fail"
	}
	//unstable
	//changed 
}
}