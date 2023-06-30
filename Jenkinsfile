pipeline {
  agent any
environment {
    SVC_ACCOUNT_KEY = credentials('dev-auth')
  }
    stages {
        
      stage('Set creds') {
            steps {
              
                sh 'echo $SVC_ACCOUNT_KEY | base64 -d > ./jenkins.json'
		            sh 'pwd'
             
            }
        }
  //stages {
    //stage("pipeline {
  //agent any

  stages {
    stage("Create VM in Dev") {
      steps {
        sh """
          gcloud compute instances create vm-develop-1 --project env-develop-demo --zone us-central1-a
         // sleep 10
          sh """
            apt-get update
            sudo su 
			apt update 
			apt -y install apache2 
			sudo service apache2 start 
			sudo update-rc.d apache2 enable
			echo "Hello World" > /var/www/html/index.html
			echo "Hello world from $(hostname) $(hostname -I)" > /var/www/html/index.html
          """
        """
      }
    }

    stage("Health Dev") {
      steps {
	   curl http://$(hostname -I)
        // Do some work on the VM
      }
    }

    stage("Create VM in UAT") {
      steps {
        sh """
          gcloud compute instances create vm-uat-1 --project env-uat-demo --zone us-central1-a
          //sleep 10
          sh """
            apt-get update
            sudo su 
			apt update 
			apt -y install apache2 
			sudo service apache2 start 
			sudo update-rc.d apache2 enable
			echo "Hello World" > /var/www/html/index.html
			echo "Hello world from $(hostname) $(hostname -I)" > /var/www/html/index.html
          """
        """
      }
    }
	stage("Health-UAT") {
      steps {
	   curl http://$(hostname -I)
        // Do some work on the VM
      }
    }
	stage("Create VM in Prod") {
      steps {
        sh """
          gcloud compute instances create vm-prod-1 --project env-develop-demo --zone us-central1-a
          //sleep 10
          sh """
            apt-get update
            sudo su 
			apt update 
			apt -y install apache2 
			sudo service apache2 start 
			sudo update-rc.d apache2 enable
			echo "Hello World" > /var/www/html/index.html
			echo "Hello world from $(hostname) $(hostname -I)" > /var/www/html/index.html
          """
        """
      }
    }
	stage("Health-Prod") {
      steps {
	   curl http://$(hostname -I)
        // Do some work on the VM
      }
    }
  }
}
    }
