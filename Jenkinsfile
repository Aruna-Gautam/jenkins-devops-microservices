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
	//agent any
	//agent{docker{image 'maven:3.6.3'} }
	agent{docker{image 'node:3.16'} }
	stages 
	{
		stage('Build')
		{
			steps {
				sh 'node --version' 
				echo "Build"
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