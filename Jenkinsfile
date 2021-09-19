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
		stage("Build Code"){
             steps{
               sh 'mvn clean package -DskipTest=True'
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