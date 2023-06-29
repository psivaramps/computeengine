pipeline {
 agent any 

	
	stages {
				
		stage ('Creating a computeengine') {
			steps {
			sh 'gcloud compute instances create instance-1 --project=gcp-sivaram-dev --zone=us-west4-b --machine-type=e2-micro --network-interface=network-tier=PREMIUM,subnet=default --maintenance-policy=MIGRATE --service-account=gcpsivaram@gcp-sivaram.iam.gserviceaccount.com --scopes=https://www.googleapis.com/auth/cloud-platform --tags=http-server,https-server --create-disk=auto-delete=yes,boot=yes,device-name=instance-1,image=projects/debian-cloud/global/images/debian-10-buster-v20211105,mode=rw,size=10,type=projects/gcp-sivaram/zones/us-west4-b/diskTypes/pd-balanced --no-shielded-secure-boot --shielded-vtpm --shielded-integrity-monitoring --reservation-affinity=any'
			
			}
		}
    }
    }
