pipeline {
    agent any

 
    stages {
          

	stage('gcloud auth') {
            steps {
                
                withCredentials([file(credentialsId: 'JENKINS-ID', variable: 'JENKINS_KEY_FILE')]) {
				  sh """
                                        gcloud version
					gcloud auth activate-service-account --key-file="$JENKINS_KEY_FILE"
					gcloud compute instances create web-host --project=hari-cloud-first-project --zone=us-central1-f --machine-type=e2-medium --metadata-from-file=startup-script=./startup-script.sh
				  """
				}
        }
	    }
     stage('instance health check'){
	     sh "gcloud compute instances describe web-host --zone=us-central1-f --format='get(networkInterfaces[0].accessConfigs[0].natIP)' > dev.txt"
             sh 'sleep 40'
             sh 'curl http://$(cat dev.txt)'
     }
		}
		}
