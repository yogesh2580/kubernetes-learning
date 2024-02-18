## **Pod**

A Pod is the smallest and most basic unit of deployment in Kubernetes. It represents a single instance of a running process within the cluster. A Pod encapsulates one or more containers, storage resources, and network settings that are tightly coupled and share the same lifecycle.

Here are some key points to understand about Pods:

### **Atomic Unit:**
 A Pod is an atomic unit of deployment in Kubernetes. It represents a single application instance or a closely related group of containers that need to be co-located and share resources.

### **Co-located Containers:**
 A Pod can contain one or more containers that are scheduled and run together on the same worker node. These containers share the same network namespace, IP address, and storage volumes. They can communicate with each other using localhost or inter-process communication mechanisms.

### **Shared Resources:**
Containers within a Pod share the same set of resources, such as CPU, memory, and storage. They can access and mount the same volumes, allowing them to share data.

### **Pod Lifecycle:**
 Pods have a lifecycle managed by Kubernetes. They are created, scheduled to a worker node, and then run until they are terminated. If a Pod fails or is evicted, Kubernetes can automatically restart or reschedule it to maintain the desired state.

### **Pod Identity:**
 Each Pod is assigned a unique IP address within the cluster, which is used for intra-Pod communication. This IP address is not exposed outside the cluster. Pods can also have a DNS name that allows other Pods to discover and communicate with them.

### **Pod Scaling:**
 Pods can be scaled horizontally by creating multiple instances of the same Pod template. Kubernetes manages the distribution of Pods across worker nodes based on resource availability and scheduling policies.

### **Pod Affinity and Anti-Affinity:**
 Kubernetes provides mechanisms to control the placement of Pods. Pod affinity allows you to schedule Pods on the same node or in proximity to other Pods, while anti-affinity ensures that Pods are not co-located on the same node.

Pods are considered to be ephemeral and disposable. They can be created, destroyed, or replaced dynamically based on scaling needs, failures, or updates. Kubernetes manages the lifecycle of Pods, ensuring that the desired state of the system is maintained.

It's important to note that Pods are not directly exposed for external access. To enable external access, Services are used to provide a stable network endpoint and load balancing for Pods.

## **Pods in Action**

There are 2 ways to create any resource in kubernetes world.

1. **Imperative:** Use a CLI command to create any k8s resource.
2. **Declarative:** Describe a desired deployment state in a [YAML](https://www.armosec.io/glossary/yaml-kubernetes/) (or JSON) file and apply the resource.

Creating a sample nginx pod
`kubectl run nginx --image=nginx --port 8080`

pod.yaml is the k8s manifest which can be used to create a pod.
[pod.yaml](./pod.yaml)

Understanding pod manifest

* apiVersion:
  v1 specifies the Kubernetes API version being used.

* kind:
  Pod indicates that this YAML describes a pod resource.
  
- metadata:
    contains metadata about the pod, including its name and labels.
  - name:
  nginx sets the name of the pod to "nginx".

  - labels:
   are key-value pairs used to identify and organize resources. In this case, the label app.kubernetes.io/name: proxy is assigned to the pod.

- spec:
    defines the specifications of the pod.

  - containers:
        is an array of containers running within the pod. In this case, there is only one container.

    - name:
        nginx sets the name of the container to "nginx".

    - image:
         nginx:stable specifies the container image to use, in this case, the stable version of the Nginx image.

    - ports:
         defines the ports to be exposed by the container.
        - containerPort: 80 specifies that the container listens on port 80.
        - name: http-web-svc assigns the name "http-web-svc" to the port.

`kubectl apply -f ./pod.yaml`