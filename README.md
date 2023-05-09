# CKA

## Minikube:

if you want to test something on your local environment or if you want to try something out very quickly for example deploying new application or new components and you want to test it on your local machine obviously setting up a cluster like this will be pretty
difficult or maybe even impossible if you don't have enough resources like memory and cpu etc and exactly for the use case there's this open source tool that is called a **minikube** so what a minikube is is basically one node cluster where the master processes and the worker processes both run on one node and this node will have a docker container runtime pre-installed so you will be able to run the containers or the pods with containers on this node


## kubectl:

so now that you have this virtual node on your local machine that represents minikube you need some way to interact with that cluster so you need a way to create pods and other kubernetes components on the node and the way to do it is using kubectl which is a **command line tool** for kubernetes cluster


## Installation of minikube:

https://minikube.sigs.k8s.io/docs/start/

## Docker Desktop:

https://www.docker.com/products/docker-desktop/

-	Now install docker desktop because however as i mentioned minikube must start either as a container or a virtual machine so we need either a container or a virtual machine tool installed on our laptop to run minikube and this is going to be the driver for minikube and opening the drivers page you see the list of supported drivers for linux mac os and windows and you see that docker is actually the preferred driver for running minikube on all operating systems


## Start minikube:

-	Once docker is **installed and running** we can switch back to the terminal and start the minikube cluster using `minikube start` command. and this may also take a while when you're running it first time because it needs to actually create the cluster and download all the necessary images and components so the next time you do minikube start it should actually go faster.
-	Now we can check the status of the cluster using `minikube status` command and we see that all the components inside are running and everything is configured
-	now start to actually interact with our cluster using command line tool and kubectl actually gets installed as a dependency when we install minikube.
-	so now i can do `kubectl get node` and this will display all the nodes in the cluster in our case we just have one node which is control plane and the worker node at the same time and we see information for each node like the status the kubernetes version that it's running as well as when it was added to the cluster
-	minikube is basically just for the startup and for deleting the cluster but everything else configuring we're going to be doing through kubectl

## Create a demo application:

Now we have enough knowledge to deploy a very simple but realistic application setup in a kubernetes cluster we will deploy a mongodb database and a web application which will connect to the mongodb database using external configuration data from config map and the secret and finally we will make our web application accessible externally from the browser.

so i have two resources here we're going to reference the kubernetes documentation to create our components which is a realistic way of working with kubernetes and also a docker hub where I have the web application image that someone created which is publicly accessible so you can also pull it directly from the docker hub in your kubernetes cluster.

Let's go ahead and create all the kubernetes configuration files that we need for deploying our application setup. 

We're going to create **four** kubernetes configuration files that we need;

1. We're going to create a config map with mongodb database endpoint
2. We're going to create a secret with username and password for mongodb
3. And then we're going to create a configuration file for deploying a mongodb application and its service
4. And then we're going to create kubernetes configuration file for deploying our simple demo app application with its service
