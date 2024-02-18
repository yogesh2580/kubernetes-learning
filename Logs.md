## **Logs & Troubleshooting**

The kubectl logs command is used to retrieve the logs of a specific pod in Kubernetes. When running the kubectl logs command, you need to provide the name of the pod you want to retrieve the logs from. Here's the basic syntax:

`kubectl logs my-pod`

By default, the kubectl logs command retrieves the logs from the main container within the pod. If there are multiple containers within the pod, you can specify the container name using the -c or --container flag. For example:

`kubectl logs my-pod -c my-container`

This command retrieves the logs from the container named my-container within the my-pod pod.

Additionally, you can use other flags with the kubectl logs command to customize the output, such as -f to stream the logs in real-time or --tail to specify the number of lines to retrieve.

`kubectl logs my-pod -c my-container -f`


### **Connecting to the pod**

To connect to a pod in Kubernetes, you can use the kubectl exec command. This command allows you to execute a command inside a running container within the pod. Here's the basic syntax:

`kubectl exec -it <pod-name> -- /bin/sh`
This command opens an interactive shell session (-it) inside the specified pod, using the /bin/sh command.

If the pod has multiple containers, you can specify the container name using the -c or --container flag. For example:

`kubectl exec -it <pod-name> -c <container-name> -- /bin/sh`
Replace <container-name> with the actual name of the container you want to connect to.