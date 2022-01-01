# mongodb-kubernetes-cluster
This is my submission to [DigitalOcean Kubernetes Challenge](https://www.digitalocean.com/community/pages/kubernetes-challenge)

# About Kubernetes and Clusters
Kubernetes (also known as k8s or “kube”) is an open source container orchestration platform that automates many of the manual processes involved in deploying, managing, and scaling containerized applications.

You can cluster together groups of hosts running containers, and Kubernetes helps you easily and efficiently manage those clusters.

Kubernetes clusters can span hosts across on-premise, public, private, or hybrid clouds. For this reason, Kubernetes is an ideal platform for hosting cloud-native applications that require rapid scaling.

# About [DigitalOcean](https://www.digitalocean.com/)
[DigitalOcean](https://www.digitalocean.com/) simplifies cloud computing so developers and businesses can spend more time building software that changes the world. With its mission-critical infrastructure and fully managed offerings, DigitalOcean helps developers, startups and small and medium-sized businesses (SMBs) rapidly build, deploy and scale applications to accelerate innovation and increase productivity and agility. DigitalOcean combines the power of simplicity, community, open source, and customer support, so customers can spend less time managing their infrastructure and more time building innovative applications that drive business growth.

# Deployment Guide 

##  Prerequisites
* [DigitalOcean Account](https://cloud.digitalocean.com/registrations/new)
* [Kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl-linux/)
* [Doctl](https://docs.digitalocean.com/reference/doctl/how-to/install/)

# Step 1 : Creating a Kubernetes Cluster on DigitalOcean
* Create a new kubernetes cluster in your project segment by clicking on the Kubernetes button in Create dropdown button on the top right.

![This is an image](https://github.com/prajalsharma/mongodb-kubernetes-cluster/blob/main/images/i4.jpg)
* Choose and fill in the following fields (choose wisely as they will affect your money consumption etc)
* For my project I chose , DataCenter:Bangalore , Nodeplan:10$/month per node , Node Count : 1,etc.  (You can choose the name for your cluster as well)
* Click on 'Create Cluster'.
* Wait for a few minutes for the cluster to be created .
![This is an image](https://github.com/prajalsharma/mongodb-kubernetes-cluster/blob/main/images/i3.jpg)

# Step 2 : Connecting to the cluster

* After node Creation,scroll down and press "Overview"
* Press "Get started!"
* In "connecting to kubernetes" , copy the command and paste it in terminal. (make sure kubectl and doctl are installed as it won't work if they aren't installed)

![This is an image](https://github.com/prajalsharma/mongodb-kubernetes-cluster/blob/main/images/i2.jpg)
* Run the copied command on your terminal.
* After it runs it will look like this on windows , if your result is same then you've connected your device with the Kubernetes Cluster.
![This is an image](https://github.com/prajalsharma/mongodb-kubernetes-cluster/blob/main/images/i1.png)
# Step 3 : Deploy a MongoDB Cluster

* Clone this repository by running the command below on your terminal 

```sh
git clone https://github.com/prajalsharma/mongodb-kubernetes-cluster.git
```

* Go to the repo directory on you local machine through terminal.
* Run ``` kubectl apply -f ``` to to deploy the MongoDB Cluster.
* Run ``` kubectl get all ``` to get the status of deployment.
* The result will look like image below , that means you've comleted this step successfully.

![This is an image](https://github.com/prajalsharma/mongodb-kubernetes-cluster/blob/main/images/i6.jpg)

# Step 4 : Verify the Deployment

* Run ``` kubectl exec deployment/mongo-client -it -- /bin/bash ``` to connect to the MongoDB cluster.
* The Command Prompt should change to root@mongo-client-xxxx
* Run ```mongo --host mongo-nodeport-svc --port 27017 -u <username> -p <password>``` where username and password are the decoded values for the base64 credentials you entered in mongodb-secrets.yaml file.
* You should see the mongoDB info and prompt for mongo commands.

![This is an image](https://github.com/prajalsharma/mongodb-kubernetes-cluster/blob/main/images/i7.jpg)

# The End 
Congratulations you've made it till the end of this repo and now the terminal will show this after ``` show dbs ``` command. You have successfully deployed a NoSQL Database on Kubernetes.
![This is an image](https://github.com/prajalsharma/mongodb-kubernetes-cluster/blob/main/images/i5.jpg)

# Miscellaneous

I have used Windows 10 for this , so people using other OS might get some errors. It was my first time using Kubernetes on DigitalOcean . Thanks to Organisers and everyone , got to learn a lot .


