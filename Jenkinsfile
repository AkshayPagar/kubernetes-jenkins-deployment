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
                  {
                  node(POD_LABEL) {
                        stage('Get a Maven project') {
                        git 'https://github.com/jenkinsci/kubernetes-plugin.git'
                        container('maven') {
                            stage('Build a Maven project') {
                                sh 'mvn -B clean install'
                    }
                }
            }
                  }
              }
	   }
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
