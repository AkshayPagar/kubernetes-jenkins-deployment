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
      podTemplate(
                  namespace: "jenkins",
                  serviceAccount: "jenkins",
                  yaml: yaml
                  containers: [
                      containerTemplate(name: 'docker', image: 'docker:stable', command: 'cat', ttyEnabled: true)
                  ],
                  volumes: [hostPathVolume(hostPath: '/var/run/docker.sock', mountPath: '/var/run/docker.sock')],
                  workspaceVolume: dynamicPVC(accessModes: 'ReadWriteOnce', requestsSize: "50Gi"),
              ) {
                  node(POD_LABEL) {
                      body()
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
