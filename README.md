# GCP Project:
____________________________________________________________________________________________________________________
### Multi-tier Architecture using Kubernetes on Google Cloud 
____________________________________________________________________________________________________________________
![](https://prnewswire2-a.akamaihd.net/p/1893751/sp/189375100/thumbnail/entry_id/0_7ljmtw18/def_height/1005/def_width/1920/version/100012/type/2/q/100)
____________________________________________________________________________________________________________________
### Objectives :
____________________________________________________________________________________________________________________
1) We have to Create two different projects such as Dev and Prod.

2) In Dev project we have to create one VPC in Singapore region while in Prod project we have to create one VPC in US region.

3) We have to connect both the VPC using VPC Peering.

4) In the Dev project : We have to launch Kubernetes Cluster using GCP Google Kubernetes Engine Service.

5) In the Prod project : We have to create MySQL Database using GCP SQL service.

6) We have to launch WordPress ,Drupal etc pod as a front-end on the top of GKE Cluster and link it with SQL database which is acting as a back-end for us.
____________________________________________________________________________________________________________________
#### Theoretical Part :
____________________________________________________________________________________________________________________
#### *Day1*
____________________________________________________________________________________________________________________
1. We know Google for its Gmail ,YouTube Google search etc . But Google also have its data center the give us to use their own availability zones buy gcp cloud that is Google cloud platform.

2. We need operating system for running an program and developers are the one who are going to run the program on the top of operating system because the purpose of operating system is to run the services that is web-server, applications ,database etc . But operating systems built on the top of hardware that hardware basically contain compute as a service that is RAM and CPU i.e compute unit ,and storage as a service that is hard disks or storage unit.

3. Suppose we are taking an example of one of the business companies such as Uber ,Netflix etc.. they can deploy their services Either on the top of their own premises or on the top of service provider. Here on-premises indicates their own Ram CPU that is their own resources and in on-premises investment is huge and here service provider refers to that one’s who provides compute as a service , provides storage as a service and the service providers is known as cloud computing. Cloud Computing platforms follow the rule of pay as we go.

4. Types of cloud computing : * Public cloud * Private cloud * Multi cloud * Hybrid cloud

5. Here we are going to talk about public cloud and we are familiar with one of the public cloud known as aws but there are more famous public cloud are also present that is GCP, azure, Alibaba etc Note : computing contain all the resources.

6. now we are going to deal with one of the most demanding public cloud known as Google cloud platform or gcp. gcp is the one who provides us resources like compute as a service ,storage as a service ,network as a service etc . Note : for provisioning the OS we have four ways — * Bare metal * Virtualization * Containerization * Cloud computing In cloud world operating system are known as instances or VM.

7. Google compute engine is one service by gcp that provides computer as a service.

8. vpc is one of the service provided by gcp for networking that provide us internal routers switches DHCP etc.

9. Storage where you install operating system is known as block storage and disc is the resource in computer engine that provide us block storage.

10. Data center : in India gcp has one region known as Asia South 1 that refers to Mumbai contain 3 availability zones such as 1A 1B and 1C that help us for disaster recovery.

11. Suppose we have two instances running one is running in the Singapore region while other is running in the Finland region .if we want these two VM is connected to each other for this public internet is not reliable here the role of Google fibre network come in Play a that is used for connectivity for transfer data from one region to other region.

12. API : it stands for application program interface every service in gcp is running with one program and that is known as API .for every services in gcp Google provide us API initially most of the API is disabled so you have to enable it.

13. There are three ways to connect to API : *Web UI : it is manual way. * CLI : it is automation. *Activate Cloud Shell : it is gcp own command prompt they launch one Linux OS for us where we can run all gcloud command. Note : we have one more way to connect to the API that is SDK (software development kit) such as python code.

14. suppose in our company organisation we are running with three teams one is working as a development team other one is as a testing team and one more is for production team . so then the role of projects in gcp come in play project give us a capability for proper management of resources for different teams we can set quota for this particular accounts for proper management of resource. WEBUI : *Go to project* Click on new project *Give name* Organisation ( for corporate world ) *Project ID ( should be unique ) CLI :* “gcloud” — it show us how many services we can manage and it is a main command that control gcp. Project is a sub command of gcloud. *“cloud projects list” — shows how many project you have.* “gcloud projects create projectid project name” — this command will help us to create a project. Note 1 : for associate your project with billing account — go to building then go to manage then just enable billing for that particular project. Note 2 : “gcloud service list — project name” this command show us which service or API has been running or enabled in that particular project Note 3 : “gcloud service enable API name — project project name” This cmd Enable API for us.

15. For launching an instance of VM we have to use Google compute engine service and follow the following steps : * Os name * Region * Machine type * Bootdisk * Attach one hard disk Note : for CLI at last they give us free created command that we can use at cloud shell.

16. Suppose we have one instance running in Singapore region and at a client side we have to log into this instance so we can use ssh protocol and a for this we require the IP username and password of that instance which is running in Singapore region. then in this instance now our inntentions is to configure the web server that is Apache httpd and and if we are using Linux system that is sent to OS version 7 for this we have to use yum install httpd command. Here yum is one command that configure whole http server for us. Then we have to create one page in /var/www/html then we have to start the httpd service and also enable it. By : Systemctl start httpd Systemctl enable httpd now you can use public IP to access to the web server working on port number 80 and for this we have to allow the firewall rule ingress as http at port 80 and ssh Port 22 and icmp for ping and we have to create firewall for http port 80 and connected to the nic card.

17. VPC : it provides network as a service vpc is like a company or we can say that it is like building and inside the vpc we have multiple subnets that is Labs. Vpc internally provide routers switches and DHCP server etc for us. If in one VPC we are running with two subnets that is lab1 and lab2 and we want to connect these two subnets or labs we have to do network peering. Suppose we have one OS running in Singapore region having one private IP and one public IP and we have one more OS running in US region also having one private IP and one public IP. but if client would like to connect to these instances they can easily connect via public network to the public IP over internet. but if we want to transfer the data from one instance to the other instance in the private world we have to use private IP and in the private world we can transfer data in the same network. if we connect two VPC the concept is known as VPC peering. vpc give us an option for vpc network peering from both sides that is from both VPC.
____________________________________________________________________________________________________________________
#### *Day2*
____________________________________________________________________________________________________________________
#### GOOGLE KUBERNETES ENGINE
____________________________________________________________________________________________________________________
GCP provide us many service and one of the many service is Google kubernetes engine. Now we have to know how kubernetes work:
`KUBERNETES`

• one use case is — if your OS running with the webserver goes down i.e completely terminated so there will be a huge lose in business and any of the client try to access your website , it fails . For this kind of scenario we need a program that keep on monitoring that particular OS and if OS terminated this program sends notification to the team and then the team contact to docker and again launch the same OS but this part is manual. I want instead my program i.e code sends notification to human beings to Launch one more OS, these program automatically launch OS within a milisecond.

• If you want fault Tolerance type of infrastructure you need that monitoring program then kubernetes role come in play. Kubernetes is a tool or program that has an inbuilt capability to keep on monitoring the container. docker has its own product for monitoring i.e swarm but kubernetes is more powerful than swarm.

• another use case is — if your OS running with the webserver so your webserver has a limit that is in 1 second it can accommodate 100 clients only but suddenly your getting 1000 of clients in 1 second and they are not able to connect , your site is showing error server time out so rather we launch one more OS again we can run program , as soon as no of request comes up i.e clients suddenly increases our program automatically launch one more OS for us and if client decreases code terminate that OS. Here we are doing scaling if client increase our program add new OS that is scale in while if client decreases our program terminate that OS that is scale out. And if your requirements is to increase RAM,CPU,HD, Network card etc that is scale up while if your requirements is to decrease RAM,CPU,HD, Network card etc that is scale down. • Scale in and Scale out are the part of horizontal scaling while scale up and scale down are the part of vertical scaling. Program who manages scaling is known as kubernetes

• One more use case is : if we are running with three OS having webserver ,the biggest challenge here is we don’t know the IP , what new IP comes when new OS launched by a program and we don’t want to give 100 of IPs to the client..

• so again we write a code and provide one IP i.e node IP to the client and tell them suppose IP 100 is a webserver. If somebody come to IP 100 behind the scene IP 100 goes to IP 1 and deploy the webserver for client and for balancing the load .. when the next client comes to IP 100 send them to IP 2 and deploy the webserver and so on and the program which is doing Load balancing for us is known as Kubernetes.

kubernetes : *It manages fault Tolerance part.* It manages auto scaling part . *It manages load balancing part . And tone’s of use case’s managed by kubernetes.

• clustering : *If you have one or more master and multiple slaves and they work together this kind of set up is known as multinode cluster.* If you have one node and both master and slave are using this node this kind of set up is known as singlenode cluster • minikube: *It is just a program to install kubernetes.*It setup the clusters.* It make things very easy • minikube Commands * minikube start — when you run this command first time .. it download the iso file and create the VM and install it for you and second time it starts minikube services. Note — in kubernetes when we launch container it is known as pod.

kubernetes commands * Kubectl : it is client command and it connects you to the kube cluster. * Kubectl get pods : it shows how many pods are running. * Kubectl launch deployment : it launch container using image. * Kubectl delete pods : it terminates pods. * Kubectl describe pods : it gives information about pods. * Kubectl expose deployment : it connect to the outside world. * Kubectl get all : it shows services information, desired , current , ready etc. * Kubectl scale deployment : it provide replicas i.e copy of OS. * Kubectl delete pods -all : it deletes all pods.

POD : * It is not at all equal to container. * Pod contain containers. * It is the main unit of kube. * Kube always monitor your pod. * Inside the pod we have containers. * Pod is the only one who manages your containers&contact DE to launch container • Kubectl run : it only launch pod.. this time lube don’t support for fault Tolerance only this power comes from deployment.

• Kubectl : it is a client program . They only bother about where is your master because they always connect to the master node . Kubectl first always go to the config file.

• kube API server program : it listen to the client and ask kubectl what they want and 8443 is the fixed port for API.

• For config file you need CA, CRT and key for authentication. Note : some of the information I also provide related to minikube.

But how our frontend server came to know the IPs of differents pods , here we use the register concept . Either we manually register the backend servers IPs to the frontend server or we automatically register them and we know today is the world of automation so we always go for automated way. Load balancer is very intelligent whenever we launch one new pod that pod IP will be automatically register to the frontend server and that concept is known as automated discovery. Note : * Frontend server ip:port is known as end point. * We use round robin mechanism for the load balancer.

For aws — we use ELB i.e elastic load balancer for creating load balancer. ELB is a subservice of EC-2. For k8s — we use services for creating load balancer.

• There are three types for services available depend upon use case : * ClusterIP — it always works inside the cluster i.e it work in a isolate way. If we have use case we don’t want to provide outside connectivity to the clients . In this kind of use case we have to create service i.e load balancer known as clusterIP * NodePort — when your POD will have outside connectivity then we have to expose it and we have to create one service type know as NodePort. * LoadBalancer — it is a one type of service which balances the node between two ports. Mostly used in multinode clusters

Google kubernetes engine provides one command to connect to master and slave using Windows or wherever you are g-cloud program running then you can run all the kubernetes command using kubectl such as Kubectl get nodes Kubectl get pods Kubectl get ns

• replica are the one that do horizontal scale in for scale out for us.

• gcp cloud has one load balancing service named as load balancer that is an independent service of load balancer.

• but we can also configure load balancer using kubernetes that take gcp external load balancer.

• In kubernetes world’s No load balancer is known as service.

• creating a GKE cluster : we have to set cluster basic where we set the location type as zonal or regional . In the node pools we have to set image type, machine type, boot disc , one node per zone in slave nodes

• GCP has also provided as one SQL service that we can use as a backend to connect our wordpress pod as a front end. for creating and SQL we have to provide instance ID ,root password ,location and version and we also have to set firewall rule.
____________________________________________________________________________________________________________________
#### IAM:
____________________________________________________________________________________________________________________
• initially gcp create root account for us that has all the power to do anything in any of the project this power is known as role this role is typically known owner role.

IAM is a way through which we can give access to multiple user that some user have owner power other one has view power while some other has edit power only.
____________________________________________________________________________________________________________________
#### GoogleAppEngine:
____________________________________________________________________________________________________________________
• it provide us platform as a service which is useful for developer to test the codes.

>> NOW LETS JUMP TO PRACTICAL PART :

* Here you can see guys i am in my console of google cloud platform.

* Here you can see i have only one project which by default created by GCP.

>> Now our First requirement is to create two projects such as Dev and Prod.
* Here you can see by using an Cloud Shell i am creating one project named as "dev-project" having project ID "dev-project-env1"

* Here you can see project is created successfully.

* Here you can see by using an Cloud Shell i am also creating one more project named as "prod-project" having project ID "prod-project-env2"

* Here you can see my this project is also created.

* Here you can i have two more projects one is "dev-project" while other one is "prod-project".

>> Now i am going to enable billing for both the projects :
* Here you can see the billing is disabled for the project and for enabling we have to click on the action and then click on change billing.

* So here you can the billing is successfully enabled for both the projects i.e Dev and Prod.

>> dev-project :
* Here in my dev-project i am going to enable API for Compute Engine because for creating VPC network it is necessary.

* Here you can see API is enabled.

>> CREATION OF VPC FOR DEV PROJECT :
* Here you can see i am going to VPC networks.

* Now we have to create new VPC network .. for this click on CREATE VPC NETWORK.

* Then here we have to give name for VPC , in my case i am setting it as "myvpcfordev"and for this VPC i am creating one subnet i.e lab as "sub-lab1".

* Here i am launching this VPC in singapore region i.e "asia-southeast1" and setting IP address range as "10.0.10.0/24".

* Then just click on create and VPC will be created ..

* Here you can see "myvpcfordev" is successfully created.

>> prod-project :
* Here in my prod-project i am also enabling the compute engine API.
* Here you can see it is successfully enabled.
____________________________________________________________________________________________________________________
#### CREATION OF VPC FOR PROD PROJECT :
____________________________________________________________________________________________________________________
* Go to the VPC networks.
* Click on CREATE VPC NETWORK for creating new VPC.

* Here i am setting my vpc name as "myvpcforprod" and for this VPC i am setting one lab or subnet as "subnet-lab2".

* Here i am launching this VPC in US region i.e "us-east1" and setting IP address range as "10.0.0.0/24".

* Here just click on create and VPC will be created.

* Here you can "myvpcforprod" is created successfully.
____________________________________________________________________________________________________________________
>> VPC PEERING :
____________________________________________________________________________________________________________________
~ dev-project :
* Here we have to go to VPC network peering in the VPC network and click on CREATE CONNECTION.

* Click on Continue.

* Here i am setting "vpc-peering-dev" as a peering name and my vpc network for dev project is "myvpcfordev" and i am peering this VPC network with another project VPC i.e prod project VPC.

* Here you can see peering is created but it is inactive because we have to create vpc peering from prod project end also for connectivity.
____________________________________________________________________________________________________________________
~ prod-project :
* Go to VPC networking peering and click on CREATE CONNECTION.

* Here i am setting "vpc-peering-prod" as a peering name and my vpc network for dev project is "myvpcforprod" and i am peering this VPC network with another project VPC i.e dev project VPC.

* Here you can see peering is created and status is also active because now both the VPC has connectivity through peering.
____________________________________________________________________________________________________________________
>> INSTALLATION OF GOOGLE SDK :
____________________________________________________________________________________________________________________
* Download Google Cloud SDK and open it.

* Click on run.

* Click on next.

* Click on I Agree.

* Click on next.

* Click on next.

* Click on next.

* Click on finish.

* Here type : y

* Here choose an Google Account.

* Now i am authenticated with the Google Cloud SDK !

* Here you can see i am running one command "gcloud project list" .. it show me all the project in my account.
____________________________________________________________________________________________________________________
>> In the Dev project : I am going to launch Kubernetes Cluster using GCP Google Kubernetes Engine Service.
____________________________________________________________________________________________________________________
* Here click on kubernetes Engine.

* Here you can see Kubernetes Engine API is enabling.

* Here you can see now the API is enabled and we got the the option for creating a Kubernetes Cluster.

* Here i am going to NODE POOLS

* Here i am setting number of nodes as "1".

* at the Nodes i am using machine type as "N1"

No alt text provided for this image
* Here in the cluster Basics i am setting location type as "regional" ,allocating "asia-southeast1" as a region and give cluster an name as "k8s-cluster-wp".

* Here i am setting the lab as "sub-lab1".

* Here you can see my kubernetes cluster using GKE has been configured.

* Here you can see in the VM instances my 3 slaves node is actively running.

* For connecting to this cluster using windows command line we have to copy this command , which is given by our cluster.

* Paste that command in windows command line and hit enter.

* Here you can see KubeConfig entry is generated for k8s-cluster-wp.

* By "kubectl get pods" command you can see there is no pods or no resource found in the default namespace.

* By "kubectl get nodes" command you can see i have 3 slave nodes or worker nodes.
____________________________________________________________________________________________________________________
>> Deploying WordPress on the top of K8S Cluster.
____________________________________________________________________________________________________________________
* Recently there is no pods.

* By "kubectl create deployment wordpress-pod --image=wordpress-5.1.1-php7.3-apache" this command i have created one pod named as "wordpress-pod".

* By "kubectl get pods" command, you can see my pod status is running.

* Here you can the whole details of your k8s cluster by "kubectl get all -o wide" command it shows us about replica set , in which slave your pod is running and it also show us service .

* Here you can see by "kubectl get svc" commabd about the service of k8s and here one service is by default active by k8s.

* In the dev project go to load balancing service.

* Here you can see there is no load balancer.

* By - "kubectl expose deployment wordpress-pod --type=LoadBalncer --port=80" command i am exposing my wordpress pod to the outside world and k8s service load balancer internally contact to the load balancer of GCP and launch one load balancer for us.

* Here you can see load balancer is launched .

* By "kubectl get svc" command you can see load balancer service is Acitve.

* Now by this EXTERNAL IP anyone from the outside world can access my wordpress site.

* Click on continue.

* before clicking on lets go ! we have to think about the database for this now i am switching my project to prod and where i am going to launch mysql database and link it with the wordpress.
____________________________________________________________________________________________________________________
>> In the Prod project : I am going to create MySQL Database using GCP SQL service.
____________________________________________________________________________________________________________________
* Go to Cloud SQL Instances and Click on Create Instance.

* Then click on Choose MySQL.

* Here i am setting instance ID as "sql-database" , root password , region as "us-east1" with b data center or zone and i am using version 5.7 of MySQL.

* By clicking on create you will see your instance is being created.

* You can see my "sql-database" has been created and having one public ip.

* Here i am going inside the connections.

* and setting an firewall as allow all where i set network cidr as 0.0.0.0/0 .

* Then just click on save.

* Here i am going to create an new user for my database for this , we have to click on ADD USER ACCOUNT .

* and here i am setting username and password , then click ADD.

* Here you can see "Vedant" user has been created.

* Now go to databases and click on CREATE DATABASE for creating new database.

* Here i am setting database name as "mydb"

* and here you can see my "mydb" database has been created.

* Guys here can see the option "connect using cloud shell", Just click on it , it will active cloud shell for us to connecting with SQL database using root user.

* Here you can see i have a proper connectivity with SQL database using root user.

* Here you can see i am able to see my "mydb" database by "show databases ; " command.

>> i also test this same for "Vedant" user.
____________________________________________________________________________________________________________________
>> NOW EVERYTHING WILL BE DEPLOYED OR CONFIGURE NOW MY MAIN INTENTION IS TO RETRIEVE THE PUBLIC IP, USERNAME , AND PASSWORD OF SQL DATABASE THAT IS IN TECHNICAL WAY I HAVE TO LINK SQL DATABASE WHICH IS MY BACKEND TO THE WORDPRESS SITE WHICH IS MY FRONTEND.
____________________________________________________________________________________________________________________
* Here from my "sql-database" i am copying the public ip and i know my username as "aaditya" and i set one password as "mickey" just for testing.

* So you can see here i fill all the details of my SQL database that will link SQL which is running in US region or in prod project with the wordpress which is running in the singapore region or in dev project.

* Just click on run the installation.

* Set the details and install wordpress.

* Provide the login details.

* You can see my wordpress is opened successfully and behind the scene it is storing all the information in the SQL database and i am going to write the blog.

* Then just publish it.

* After publishing you will get one link from which you can access your wordpress site.

* Here you can see guys WordPress site is deployed.

* Here i am login into MySQL as "aaditya" and you can see i have one database named as "mydb".

* For changing the database i am using "use mydb" command and you can see Database changed.

* By show tables; command you can see the tables in "mydb" database.

* Here i am scale out my wordpress-pod and setting 5 replicas.

* You can see four more pods has been launched.

* Here you can find extra details of the pods like in which slave nodes they are running.
____________________________________________________________________________________________________________________
### Author:
----------------------------------
```diff
+ Dipaditya Das | DipadityaDas@gmail.com
```
