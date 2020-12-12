pipeline {
   agent {
      docker { image 'python:3.7' }
   }
   stages {

   	stage('Version') { 
            steps{
 		echo "stage-Version"
		sleep(12)
	  //build job: 'version-check'
          }
   	}

   	stage('Environment') {
            steps{
               echo "stage-environment-check"
	       sleep(10)
       		// build job: 'environment-check'
          }
   	}
   }
}
