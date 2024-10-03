pipeline {
    agent any

 
    stages {
          

	stage('gcloud auth') {
            steps {
                
                withCredentials([file(credentialsId: 'JENKINS-ID', variable: 'JENKINS_KEY_FILE')]) {
				  sh """
					gcloud compute instances create web-host --project=hari-cloud-first-project --zone=us-central1-f --machine-type=e2-medium --metadata-from-file=startup-script=./startup-script.sh
				  """
				}
        }
	    }
		}
		}
