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


![image](https://github.com/aicloudpost/kubernetes-installation/assets/166476986/3726bce7-677d-4860-ade1-ac0dee491759)


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

**Prerequisites (recommended but resource specification may change depending on your workloads)
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

**
