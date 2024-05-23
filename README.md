# Kubernetes-installation
Installation details: Kubernetes installation using kubeadm (cni=calico, cri=cri-o, os=ubuntu22.04)
########################################################################

Install Kubernetes Cluster on Ubuntu 22.04
--------------------------------------------
A Kubernetes cluster comprises a master node (control plane) and worker nodes. We generally run application workload on worker nodes and master nodes are used as the control plane, as it manages the worker nodes and pods in the cluster.
Kubernetes is a popular container orchestration tool.

Features:
----------------
	Load balancing.

	Self-healing

	High availability/ensure no downtime/maintain fault tolerance

	Performance enhancement

	Auto-scaling.


Kubernetes Terminologies
----------------------------
**Pod:** It represents one or more containers running in a cluster.

**Service:** An abstract way to access pod/application.

**Namespace:** It removes name collision within a cluster. It supports multiple virtual clusters on the same physical cluster.

**Node:** Kubernetes worker machine.

**Cluster:** Consisting of a group of nodes running containerized applications on Kubernetes.

**ReplicaSets:** Several replicas of running pods. It helps in achieving high availability and scalability.

**Label:** Giving a name to Kubernetes objects so that they can be identified across the system.

**Kubelet:** An agent runs on each node and checks if the containers are running in the pods.

**Kubectl:** Command-line utility to interact with the Kubernetes API server.

**Kube-proxy:** Network proxy which contains all the network rules on each node in the cluster.

![kubernetes-architecture](https://github.com/aicloudpost/kubernetes-installation/assets/166476986/75f72074-1fa8-4610-b0fe-4ee92b212258)


Kubernetes follows master-slave architecture. Kubernetes architecture has a master node and worker nodes. 

**There are four components of a master node components:**

	Kube API server

	Controller

	Scheduler

	etcd

**The worker node has three components:**

	Kubelet

	kube-proxy

	container runtime

**There are several ways to install Kubernetes, including**

•	Single-node installation: Good for development, testing, and practices, or previewing Kubernetes.

•	Unmanaged Kubernetes installation: You manage everything yourself, as it's not managed by a cloud vendor.

•	Kubespray: A combination of Ansible and Kubernetes that provides deployment flexibility.

•	Kubeadm: A popular method that's good for multi-node clusters and real-time setups.

•	Kops: An open-source tool that's good for managing and creating small-scale, production-grade clusters.

•	Minikube: A free, open-source tool that runs a single-node cluster in a virtual machine on your laptop.

**Prerequisites (recommended but resource specification may change depending on your workloads)**
-------------------------------------------------------------------------------------------
•	Minimal install of Ubuntu 22.04

**Master:**
-----------
  	RAM: 2Gi or more

  	Cores/Vcpu: 2 or more

  	Storage: 20 Gig

**Worker:**
-----------
  	RAM: 1Gi or more

  	Cores/Vcpu: 2 or more

  	Storage: 20 Gig

•	Sudo user with admin rights

•	Internet connectivity on each node

Note: provision EC2 nodes and let’s proceed further for installation.


**Overall, installing Kubernetes on Ubuntu involves steps such as:**

1)	Disabling swap;
   
3)	Setting up hostnames;
   
5)	Setting up the IPV4 bridge on all the nodes;
   
7)	Installing Kubernetes components on all the nodes;
   
9)	Installing Docker or a suitable containerization tool on all the nodes;
    
11)	Initializing the Kubernetes cluster using kubeadm on the Master node;
    
13)	Install the Calico network plugin (operator) on the Master node.
    
15)	Join the worker nodes to the master node (control plane) using the join command.
    

**Kubeadm Setup Prerequisites**

Following are the prerequisites for Kubeadm Kubernetes cluster setup.

1)	Minimum two Ubuntu nodes [One master and one worker node]. You can have more worker nodes as per your requirement.
   
3)	The master node should have a minimum of 2 vCPU and 2GB RAM.
   
5)	For the worker nodes, a minimum of 1vCPU and 2 GB RAM is recommended.
   
7)	10.X.X.X/X network range with static IPs for master and worker nodes. We will be using the 192.x.x.x series as the pod network range that will be used by the Calico network plugin. Make sure the Node IP range and pod IP range don’t overlap.
   
Note: If you are setting up the cluster in the corporate network behind a proxy, ensure set the proxy variables and have access to the container registry and docker hub. Or talk to your network administrator to whitelist registry.k8s.io to pull the required images.
Kubeadm Port Requirements.

Please refer to the following image and make sure all the ports are allowed for the control plane (master) and the worker nodes. If you are setting up the kubeadm cluster cloud servers, ensure you allow the ports in the firewall configuration.

**Control plane**
Protocol	Direction	Port Range	Purpose	Used By

![image](https://github.com/aicloudpost/kubernetes-installation/assets/166476986/a8e18820-32df-4d4e-aecb-d8ef2d1da07b)


Although etcd ports are included in control plane section, you can also host your own etcd cluster externally or on custom ports.

**Worker node(s)**

Protocol	Direction	Port Range	Purpose	Used By

![image](https://github.com/aicloudpost/kubernetes-installation/assets/166476986/c6c8e19b-042c-447d-b9a8-cce41bda63bd)

Default port range for NodePort Services.

All default port numbers can be overridden. When custom ports are used those ports need to be open instead of defaults mentioned here.

One common example is API server port that is sometimes switched to 443. Alternatively, the default port is kept as is and API server is put behind a load balancer that listens on 443 and routes the requests to API server on the default port.


