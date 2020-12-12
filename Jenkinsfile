pipeline {
   agent {
	   kubernetes{
	   	    cloud 'kubernetes'
		      label nodelabel
  		    yaml """
  		    spec:
            securityContext:
                fsGroup: 1000
          containers:
          - name: jnlp
            env:
              - name: HOME
                value: /home/jenkins
            securityContext:
              fsGroup: 1000
              runAsGroup: 1000
              runAsUser: 1000
          """
      podTemplate(containers: [
                      containerTemplate(name: 'maven', image: 'maven:3.3.9-jdk-8-alpine', ttyEnabled: true, command: 'cat')
                  ]) 
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
