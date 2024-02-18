## **Minikube**
Minikube is a tool that allows you to run a single-node Kubernetes cluster locally on your machine. It is designed to simplify the process of setting up and testing Kubernetes applications without the need for a full-scale production cluster. Minikube provides an easy way to learn and experiment with Kubernetes features and workflows in a local development environment.

Here are some key aspects of Minikube:

### **Local Kubernetes Cluster:**
Minikube creates a lightweight, single-node Kubernetes cluster on your local machine. It runs a virtual machine (VM) using a hypervisor like VirtualBox, VMware, or HyperKit, depending on your operating system. This local cluster behaves similarly to a full-scale Kubernetes cluster, allowing you to deploy and manage applications using the same Kubernetes APIs and tools.

### **Easy Setup and Configuration:**
Minikube simplifies the setup process by automating the installation of the necessary dependencies, such as the Kubernetes binaries, container runtime, and a compatible hypervisor. It provides a command-line interface (CLI) that allows you to start, stop, and manage the local cluster effortlessly.

### **Isolated Development Environment:**
With Minikube, you can create an isolated development environment on your machine. This allows you to test and iterate on your Kubernetes applications without impacting other environments or production clusters. You can deploy and manage your applications within the Minikube cluster, ensuring consistency and reproducibility.

### **Support for Kubernetes Features:**
Minikube supports a wide range of Kubernetes features, allowing you to experiment with various capabilities of the platform. This includes deploying and scaling applications, creating and managing services, configuring storage, setting up networking, and exploring advanced features like secrets, ingress, and RBAC.

## **Installing minikube on macOS**

#### Prerequisite
Docker/ Docker desktop should be running

We can install minikube using brew package manager

`brew install minikube`

Few useful commands for interacting with minikube cluster
```
minikube start 

minikube status

minikube dashboard

minikube stop

minikube pause

minikube unpause

```