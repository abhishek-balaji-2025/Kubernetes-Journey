# Kubernetes Pod Commands for Beginners

This guide covers essential Kubernetes commands focused on managing pods, designed specifically for beginners. It provides straightforward explanations and examples to help you create, inspect, debug, and manage pods effectively in your Kubernetes cluster.

---

## 1. View All Nodes in the Cluster

`kubectl get nodes`

**Functionality:**  
Displays a list of all nodes (machines or servers) in the Kubernetes cluster. It includes details such as node name, status, role (e.g., master/worker), and the Kubernetes version running on each node.

---

## 2. Create a New Pod

`kubectl run <pod-name> --image=<image-name>:<version>`

**Example:**  
`kubectl run myfirstpod --image=ubuntu:latest`

**Functionality:**  
Creates a new pod named `myfirstpod` using the specified Docker image (`ubuntu:latest`). The container will be based on this image and run inside the newly created pod.

---

## 3. Display All Pods

`kubectl get pods`

**Functionality:**  
Lists all pods in the current namespace along with their status (e.g., Running, Pending, CrashLoopBackOff).

---

## 4. Display Pods with Additional Information

`kubectl get pods -o wide`

**Functionality:**  
Displays all pods with extra details such as the node they’re running on, their IP addresses, and the container image used.

---

## 5. Get Detailed Information About a Pod

`kubectl describe pod <pod-name>`

**Functionality:**  
Shows detailed information about a specific pod, including events, environment variables, volume mounts, restart count, and more. Useful for debugging.

---

## 6. Delete a Pod

`kubectl delete pod <pod-name>`

**Example:**  
`kubectl delete pod myfirstpod`

**Functionality:**  
Deletes the specified pod from the cluster. Useful for removing a pod that is crashing or no longer needed.

---

## 7. View Logs from a Pod

`kubectl logs <pod-name>`

**Example:**  
`kubectl logs pod2`

**Functionality:**  
Displays the logs (standard output and standard error) of the main container in the specified pod. Helps in understanding what the application inside the pod is doing or why it's failing.

---

## 8. Access the Shell Inside a Pod

`kubectl exec -it <pod-name> -- /bin/bash`

**Functionality:**  
Starts an interactive shell session inside the pod’s container. Useful for manual inspection, running commands, or debugging from inside the container. Use `/bin/sh` if `/bin/bash` is not available.

---

## 9. Test Pod Connectivity

`curl <pod-IP>:80`

**Functionality:**  
Sends an HTTP request to port 80 of the given pod IP. This is useful for testing whether the service or application running inside the pod is reachable and responding correctly.
