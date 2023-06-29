pipeline {
 agent any 

	
	stages {
				
		stage ('Creating a computeengine') {
			steps {
			sh 'gcloud compute instances create gce-vm-dev1 --project=sivaram-dev-382816 --zone=us-west4-b --machine-type=e2-small --network-interface=network-tier=PREMIUM,stack-type=IPV4_ONLY,subnet=default --metadata=startup-script=#!/bin/bash$'\n'apt\ update\ $'\n'apt\ -y\ install\ apache2$'\n'echo\ \"Hello\ world\ from\ \$\(hostname\)\ \$\(hostname\ -I\)\"\ \>\ /var/www/html/index.html$'\n' --maintenance-policy=MIGRATE --provisioning-model=STANDARD --service-account=47244189395-compute@developer.gserviceaccount.com  --tags=http-server --create-disk=auto-delete=yes,boot=yes,device-name=gce-vm-dev,image=projects/debian-cloud/global/images/debian-11-bullseye-v20230615,mode=rw,size=10,type=projects/sivaram-dev-382816/zones/us-west4-b/diskTypes/pd-balanced --no-shielded-secure-boot --shielded-vtpm --shielded-integrity-monitoring --labels=env=dev,goog-ec-src=vm_add-gcloud --reservation-affinity=any'
			
			}
		}
    }
    }
