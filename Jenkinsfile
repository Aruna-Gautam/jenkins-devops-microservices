// node {
// 	stage('Build') {
// 		echo "Build"
// 	}
// 	stage('Test') {
// 		echo "Test"
// 	}
// }

//surefire-   unit test
//failsafe- integration test

pipeline 
{
	agent any
	environment {
		
		dockerHome = tool 'myDocker'
		mavenHome = tool 'myMaven'
		PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"
	}
	//agent{docker{image 'maven:3.6.3'} }
	//agent{docker{image 'node:12.18.3'} }
	stages 
	{
		stage('Checkout')
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
		stage('Compile')
		{
			steps {
			sh "mvn clean compile"
			}
		}
		stage('Test')
		{
			steps {
			sh "mvn test"
		} 
		}

		stage('Intergration Test')
		{
			steps {
			sh "mvn failsafe:integration-test failsafe:verify"
		} 
		}

		stage('Package')
		{
			steps {
			sh "mvn package -DskipTests"
		} 
		}

		stage('Build docker image')
		{
			steps {
				script{
					dockerImage = docker.Build("148415/currency-exchange-devops:${env.BUILD_TAG}")
				}			
		} 
		}

		stage('Push docker image')
		{
			steps {
				script{
					docker.withRegistry('', 'dockerhub')
					dockerImage.Push();
					dockerImage.Push('latest');
				}
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



