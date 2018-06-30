1.Architecture Diagram



2. Master

Master is the physical machine/VM that runs the control plane components of the kubernetes. Master components provide the cluster’s control plane. Master components make global decisions about the cluster (for example, scheduling), and detecting and responding to cluster events (starting up a new pod when a replication controller’s ‘replicas’ field is unsatisfied).

Master Components

Api Server:

API server is  the gateway that exposes Kubernetes API, The kubernetes api is the interface for the cluster applications to interact with the kubernetes cluster and  perform  all the operations on cluster.


Controllers & controller managers:
The main pfunction of the controllers is to mke th current state of the cluster to the desired state.
The controllers can be divided in to two logical types.

The controllers are part of two process called
1. Kube control manager
2. Cloud control manager


kube control manager :

is a process implementing the below control loops

Replication Controller: Responsible for maintaining the correct number of pods for every replication controller object in the system.

Endpoints Controller: Populates the Endpoints object (that is, joins Services & Pods).

Service Account & Token Controllers: Create default accounts and API access tokens for new namespaces.
