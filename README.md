# kubernetes-learning
Repository for learning basics of kubernetes using minikube

## **What is kubernetess?**

Kubernetes is an open source orchestration platform.

orchestration refers to the management and coordination of multiple containers deployed across clusters. It involves Automating deployment, scaling, Networking, Health monitoring and self healing and rolling updates and roll back.

### **Deployment:**
we define the desired state of our application, k8s takes care of scheduling of containers on the appropriate nodes depending upon the resource availability and affinity rules

### **Scaling:**
depending upon the scaling rules and policies k8s will scale in or scale out based on CPU utilization, memory usage or any custome metric we define.

### **Health Monitoring:**
k8s continously monitors the health of the container, if the container becomes unhealthy, crashes or unreachable k8s will restart the container automatically 

### **Rolling update and Rollbacks:**
k8s support rolling updates, allowing you to update containerized applications without downtime.

### **Networking:**
They provide features like service discovery and load balancing, allowing containers to communicate with each other easily. Containers can be grouped together as services and exposed via a single endpoint, simplifying networking configurations.


## Kubernetes Architecure

[Refer this page](./Architecture.md)

### Other userful Resources

[Minikube](./Minikube.md)

[Pods](./pods/Pod.md)

[Deployments](./deployment/Deployment.md)

[Services](./service/Service.md)

[Namespaces](./namespace/Namespace.md)

[Logs & Troubleshooting](./Logs.md)