pipeline {
    agent any

    environment {
    DEV_SVC_ACCOUNT_KEY = credentials('dev-auth')
    UAT_SVC_ACCOUNT_KEY = credentials('uat-auth')
    PROD_SVC_ACCOUNT_KEY = credentials('prod-auth')
  }
     
    stages {
	stage('Deploy on DEV') {
	 steps {
    sh 'echo $DEV_SVC_ACCOUNT_KEY | base64 -d > dev.json'
    sh 'cd Jenkins'		 
    sh 'gcloud auth activate-service-account env-develop-demo@env-develop-demo.iam.gserviceaccount.com --key-file=dev.json' 
    sh 'gcloud config set project env-develp-demo'
    sh 'gcloud compute instances create springapp --zone=us-central1-a --tags=http-server --metadata-from-file=startup-script=./scripts/startup-script.sh'
    sh "gcloud compute instances describe springapp --zone=us-central1-a --format='get(networkInterfaces[0].accessConfigs[0].natIP)' > dev.txt"
	  sh 'cat dev.txt'    
    }
    }   
    
  
  stage('DEV App health check') {
	 steps {
            sh 'sleep 40'
	    sh 'curl http://$(cat dev.txt)'
    
    }
    }
      
      stage('Deploy on UAT') {
	 steps {
    
      sh 'echo $UAT_SVC_ACCOUNT_KEY | base64 -d > uat.json'
      sh 'gcloud auth activate-service-account siva-jenkins@sivaram-dev-382816.iam.gserviceaccount.com --key-file=uat.json'
      sh 'gcloud config set project sivaram-dev'
      sh 'gcloud compute instances create springapp --zone=us-central1-a --tags=http-server --metadata-from-file=startup-script=./scripts/startup-script.sh'
      sh "gcloud compute instances describe springapp --zone=us-central1-a --format='get(networkInterfaces[0].accessConfigs[0].natIP)' > uat.txt"
	    sh 'cat uat.txt'
        
    }
    }
       stage('UAT App health check') {
	 steps {
            sh 'sleep 40'
	    sh 'curl http://$(cat uat.txt)'
    
    }
    }
      
      stage('Deploy on PROD') {
	 steps {
    
      sh 'echo $PROD_SVC_ACCOUNT_KEY | base64 -d > prod.json'
      sh 'gcloud auth activate-service-account env-prod-demo@env-prod-demo.iam.gserviceaccount.com --key-file=prod.json'
      sh 'gcloud config set project env-prod-demo'
      sh 'gcloud compute instances create springapp --zone=us-central1-a --tags=http-server --metadata-from-file=startup-script=./scripts/startup-script.sh'
      sh "gcloud compute instances describe springapp --zone=us-central1-a --format='get(networkInterfaces[0].accessConfigs[0].natIP)' > prod.txt"
	    sh 'cat prod.txt'
        
    }
    }
       stage('PROD App health check') {
	 steps {
            sh 'sleep 40'
	    sh 'curl http://$(cat prod.txt)'
    
    }
    }
   }
}
