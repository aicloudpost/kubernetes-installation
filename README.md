# Kubernetes-installation
Installation details: Kubernetes installation using kubeadm (cni=calico, cri=cri-o, os=ubuntu22.04)
####################################################################################################

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
****Cluster:** Consisting of a group of nodes running containerized applications on Kubernetes.
**ReplicaSets:** Several replicas of running pods. It helps in achieving high availability and scalability.
**Label:** Giving a name to Kubernetes objects so that they can be identified across the system.
**Kubelet:** An agent runs on each node and checks if the containers are running in the pods.
**Kubectl:** Command-line utility to interact with the Kubernetes API server.
**Kube-proxy:** Network proxy which contains all the network rules on each node in the cluster.
