
Container
---------
A container image is a lightweight, stand-alone, executable package of a piece of software that includes everything 
needed to run it: code, runtime, system tools, system libraries, settings

Container Spec:


spec:
      containers:
             - name: nginx
              image: nginx
            ports:
            - containerPort: 80
 imagePullSecrets:
  - name: myregistrykey
  
        
 Kubernetes Container Image Pull:
 -------------------------------
 Kubernetes supports the docker containers natively. The docker image is built by using the docker file ,
 Once the docker image is created the image is pushed in to the repoistory.
 The docker image to be used by the kubernetes is mentioned in the container spec.
 The kubelet sees the image name in the container spec and uses the latest tag by default to pull the image.
 Once the image is pulled the kubelt starts the container.

Updating Images
---------------

The default pull policy is IfNotPresent which causes the Kubelet to skip pulling an image if it already exists. If you would like to always force a pull, you can do one of the following:

set the imagePullPolicy of the container to Always;
use :latest as the tag for the image to use;

Using a Private Registry
------------------------
Private registries may require keys to read images from them. Credentials can be provided in several ways:

Specifying ImagePullSecrets on a Pod
-------------------------------------
only pods which provide own keys can access the private registry Each option is described in more detail below.


Specifying ImagePullSecrets on a Pod
------------------------------------
Note: This approach is currently the recommended approach for Google Kubernetes Engine, GCE, and any cloud-providers where node creation is automated.

Kubernetes supports specifying registry keys on a pod.

Creating a Secret with a Docker Config
-------------------------------------
Run the following command, substituting the appropriate uppercase values:

$ kubectl create secret docker-registry myregistrykey --docker-server=DOCKER_REGISTRY_SERVER --docker-username=DOCKER_USER --docker-password=DOCKER_PASSWORD --docker-email=DOCKER_EMAIL
secret "myregistrykey" created.
If you need access to multiple registries, you can create one secret for each registry. Kubelet will merge any imagePullSecrets into a single virtual .docker/config.json when pulling images for your Pods.

Pods can only reference image pull secrets in their own namespace, so this process needs to be done one time per namespace.

