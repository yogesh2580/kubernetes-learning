## **Deployment**

In Kubernetes, a Deployment is a higher-level resource that provides declarative and scalable management for Pods. It allows you to define and manage the desired state of your application, including the number of replicas, updates, and rollbacks.

Here are the key points to understand about Deployments:

### **Declarative Configuration:**
Deployments use a declarative approach to define the desired state of your application. You specify the desired number of replicas, container images, resource requirements, and other configuration details in a Deployment manifest file or through the Kubernetes API.

### **Pod Template:** 
A Deployment manages a set of identical Pods, known as replicas. You define a Pod template within the Deployment, specifying the container image, environment variables, ports, and other settings for the Pods.

### **Scaling and Replicas:**
Deployments allow you to scale your application horizontally by specifying the desired number of replicas. Kubernetes automatically creates and manages the specified number of Pods, distributing them across the worker nodes in the cluster.

### **Rolling Updates and Rollbacks:**
Deployments support rolling updates, allowing you to update your application without downtime. When you update the Pod template or container image in a Deployment, Kubernetes gradually replaces the existing Pods with the new ones, ensuring a smooth transition. If any issues arise during the update, you can easily roll back to the previous version.

### **Health Checks:**
Deployments include support for health checks, which allow Kubernetes to monitor the health of Pods. You can define readiness probes and liveness probes to determine if a Pod is ready to receive traffic or if it needs to be restarted.

### **Versioning and History:**
Deployments maintain a revision history of changes made to the Pod template. This allows you to track and manage different versions of your application, making it easier to roll back to a previous version if needed.

### **Scaling Strategies:**
Deployments support different scaling strategies, such as manual scaling, automatic scaling based on resource utilization, or scaling based on custom metrics using Horizontal Pod Autoscaling (HPA).

Deployments provide a powerful and flexible way to manage the lifecycle of your application in Kubernetes. They abstract away the complexity of managing individual Pods and provide features like scaling, rolling updates, and rollbacks to ensure the availability and reliability of your application.

By using Deployments, you can easily manage and scale your application, perform updates seamlessly, and maintain a desired state without manual intervention.

### **Deployments in Action**

#### **Kubectl command for creating a deployment**

`kubectl create deployment hello-node --image=registry.k8s.io/e2e-test-images/agnhost:2.39 -- /agnhost netexec --http-port=8080 `

* kubectl:
  This is the command-line tool used to interact with Kubernetes clusters.

* create deployment:
  This part of the command is used to create a new deployment in Kubernetes. A deployment is a higher-level resource that manages a set of identical pods, ensuring that the desired number of replicas are running at all times.

* hello-node:
  This is the name of the deployment you are creating. You can choose any name you like for your deployment.

* --image=registry.k8s.io/e2e-test-images/agnhost:2.39:
  This argument specifies the container image to use for the pods in the deployment. In this case, the image being used is registry.k8s.io/e2e-test-images/agnhost:2.39. The image is pulled from the specified container registry and version/tag.
  
* --:
  This is used to separate the kubectl command and its arguments from the command to be run inside the container.

* /agnhost netexec --http-port=8080:
  This is the command to be executed inside the container. In this case, it is running the agnhost binary with the netexec command and specifying the

* --http-port flag with a value of 8080.
   This command is specific to the agnhost container image and may vary depending on the image you are using.


#### **Creating a deployment with manifest file**

[deployment.yaml](./deployment.yaml)

* apiVersion: apps/v1:
  This specifies the API version of the Kubernetes resource being defined, in this case, a Deployment. The apps/v1 API version is used for managing deployments.

* kind: Deployment:
  This indicates that the resource being defined is a Deployment. A Deployment manages a set of identical pods and ensures the desired number of replicas are running.

* metadata:
  This section contains metadata about the Deployment, such as its name.

* spec:
  This section defines the desired state of the Deployment.

  * selector:
  This specifies the labels used to select the pods that the Deployment manages. In this case, the pods are selected based on the label run: my-nginx.

  * replicas: 2:
  This specifies the desired number of replicas (pods) that should be running. In this case, the Deployment should maintain 2 replicas.

  * template:
  This section defines the pod template used by the Deployment.

    * metadata:
        This section contains metadata specific to the pod template.

      * labels:
            This specifies the labels to be applied to the pods created from this template. In this case, the pods will have the label run: my-nginx.
    * spec: This section defines the specification of the pod.

      * containers:
            This is an array of containers running in the pod. In this case, there is one container defined.

        * name: my-nginx:
            This specifies the name of the container.

        * image: nginx:
            This specifies the container image to use for the container. In this case, the image used is nginx.

        * ports:
            This section defines the ports to be exposed by the container.

            * containerPort: 80:
                This specifies that the container should listen on port 80.
