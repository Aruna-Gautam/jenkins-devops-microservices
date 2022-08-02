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
	stages 
	{
		stage('Build')
		{
			steps {
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
}
}