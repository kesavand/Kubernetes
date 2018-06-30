1.Architecture Diagram



[[https://github.com/kesavand/Kubernetes/blob/master/master_node_structure.png|alt=octocat]]

Master Components
------------------
Master is the physical machine/VM that runs the control plane components of the kubernetes. Master components provide the cluster’s control plane. Master components make global decisions about the cluster (for example, scheduling), and detecting and responding to cluster events (starting up a new pod when a replication controller’s ‘replicas’ field is unsatisfied).



Api Server:
----------
API server is  the gateway that exposes Kubernetes API, The kubernetes api is the interface for the cluster applications to interact with the kubernetes cluster and  perform  all the operations on cluster.


Controllers & controller managers:
---------------------------------
The main pfunction of the controllers is to mke th current state of the cluster to the desired state.
The controllers can be divided in to two logical types.

The controllers are part of two process called
1. Kube control manager
2. Cloud control manager


kube control manager :
-------------------
is a process implementing the below control loops

Replication Controller: Responsible for maintaining the correct number of pods for every replication controller object in the system.

Endpoints Controller: Populates the Endpoints object (that is, joins Services & Pods).

Service Account & Token Controllers: Create default accounts and API access tokens for new namespaces.

Cloud Control manager:
---------------------
The cloud control manager that runs controllers that interact with the underlying cloud providers, cloud-controller-manager runs cloud-provider-specific controller loops only.

The following controllers have cloud provider dependencies:

Node Controller: For checking the cloud provider to determine if a node has been deleted in the cloud after it stops responding

Route Controller: For setting up routes in the underlying cloud infrastructure

Service Controller: For creating, updating and deleting cloud provider load balancers

Volume Controller: For creating, attaching, and mounting volumes, and interacting with the cloud provider to orchestrate volumes

Node Components
---------------

Container Runtime
-----------------
The container runtime is the software that is responsible for running containers. Kubernetes supports several runtimes: Docker, rkt, runc and any OCI runtime-spec implementation.

kubelet
-------
An agent that runs on each node in the cluster. It makes sure that containers are running in a pod.
The kubelet takes a set of PodSpecs that are provided through various mechanisms and ensures that the containers described in those PodSpecs are running and healthy. The kubelet doesn’t manage containers which were not created by Kubernetes.

kube-proxy
----------
kube-proxy enables the Kubernetes service abstraction by maintaining network rules on the host and performing connection forwarding.

Addons
------
Addons are pods and services that implement cluster features. The pods may be managed by Deployments, ReplicationControllers, and so on. Namespaced addon objects are created in the kube-system namespace.

DNS
---
Cluster DNS is a DNS server, in addition to the other DNS server(s) in your environment, which serves DNS records for Kubernetes services.
Containers started by Kubernetes automatically include this DNS server in their DNS searches.

Web UI (Dashboard)
------------------
Dashboard is a general purpose, web-based UI for Kubernetes clusters. It allows users to manage and troubleshoot applications running in the cluster, as well as the cluster itself.

Container Resource Monitoring
-----------------------------
Container Resource Monitoring records generic time-series metrics about containers in a central database, and provides a UI for browsing that data.
The monitoring resources used in kubernetes are CAdvisor,Promethus
For more information see the Monitoring Section.
  
Cluster-level Logging
---------------------
A Cluster-level logging mechanism is responsible for saving container logs to a central log store with search/browsing interface.


