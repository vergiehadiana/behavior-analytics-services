
# Behavior Analytics Services Deploy on Openshift 4.x
Behavior Analytics Services (BAS) Template Deploy, ONLY Services for **Analytics Proxy Deployment** 

## Based Guide on IBM Hands-On Labs here:
[![N|Solid](https://developer.ibm.com/caas-storage/skillscollection/behavior-analytics-services/dev/_attachments/BAS_medium.png)](https://developer.ibm.com/openlabsdev/ui/behavior-analytics-services)
> BAS Quickstart Installation for MAS, Quickstart guide to install Behavior Analytics Services(BAS) for Maximo Application Suite (MAS).

## Guide :
1. Clone this repository
> **Command:** git clone https://github.com/vergiehadiana/behavior-analytics-services.git
2. Navigate to directory "Installation Scripts" to execute the script
> **Command:** cd behavior-analytics-services/
3. The "cr.properties" has the variables to create the deployment. Update the cr.properties file
> **Command:** vi cr.properties

It is mandatory to change the fields under section- "Change the values of these properties"
**Properties**	          | **Description**
--------------------------|-------------------------------------------------------------
projectName	              | Openshfit project where the BAS Operator will be installed
storageClassKafka	      | Storage class of type ReadWriteOnce
storageClassZookeeper	  | Storage class of type ReadWriteOnce
storageClassDB	          | Storage class of type ReadWriteOnce
storageClassArchive	      | Storage class of type ReadWriteMany
dbuser	                  | User name to be set for Database
dbpassword  	          | Password to be set for Database
grafanauser	              | User name to be set for Grafana
grafanapassword	          | Password to be set for Grafana

The remaining fields can be updated or kept default.
**Properties**	          | **Description**
--------------------------|-------------------------------------------------------------
storageSizeKafka	      | Size (in G) of the storage to be attached to Kafka
storageSizeZookeeper	  | Size (in G) of the storage to be attached to Zookeeper
storageSizeDB	          | Size (in G) of the storage to be attached to Database
storageSizeArchive	      | Size (in G) of the storage to be attached for saving DB archives
eventSchedulerFrequency	  | Frequency at which events will be forwarded to proxy in Cron format. It accepts values in Cron format (https://en.wikipedia.org/wiki/Cron)
prometheusSchedulerFrequency	| Frequency in Cronjob format to pull metrics from Prometheus. It accepts values in Cron format (https://en.wikipedia.org/wiki/Cron)
envType	                  | Type of environment. Can be prod (HA) or lite (non HA)
ibmproxyurl	              | URL of IBM Proxy
airgappedEnabled	      | Set value to "true" if airgapped setup is to be enabled otherwise keep the default value "false"
imagePullSecret      	  | Secret to pull container images from registry

**Save the file** 
> **Command:** ":wq"

4. Execute the script BAS_installation.sh
> **Command:** ./BAS_installation.sh

It takes **approximately 35 mins for the deployment to complete**

On successful completion, the script will print the API KEY, BAS Endpoint URL and Grafana URL on the console.
Additionally a log file "bas-installation.log" is generated for debug purpose.
