pipeline{
    agent any
    environment{
        dockerHome = tool 'myDocker'
        mavenHome = tool 'myMaven'
        PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"
    }
    stages{
        stage("Check Version"){
            steps{
               sh 'mvn --version'
               sh 'docker --version'
			   echo "Build"
			   echo "BUILD_NUMBER - $env.BUILD_NUMBER"
			   echo "BUILD_ID - $env.BUILD_ID"
			   echo "JOB_NAME - $env.JOB_NAME"
			   echo "BUILD_TAG - $env.BUILD_TAG"
            }
        }
		stage("Compile"){
             steps{
               sh 'mvn clean compile'
            }
        }
        stage("Test"){
             steps{
               sh 'mvn test'
            }
        }
        stage("Integration Test"){
             steps{
               sh 'mvn failsafe:integrstion-test failsafe:verify'
            }
        }
        
		
    }
    post{
        always{
            echo "========always========"
        }
        success{
            echo "========pipeline executed successfully ========"
        }
        failure{
            echo "========pipeline execution failed========"
        }
    }
}