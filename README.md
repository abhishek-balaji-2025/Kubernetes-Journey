# Kubernetes Learning Journey 🚀

Welcome to my **Kubernetes repository** – a personal logbook of my hands-on learning experience with container orchestration using Kubernetes. This repo captures my progression from foundational concepts to real-world implementations. 

Inside, you'll find:

- ✅ Step-by-step deployments  
- 📄 YAML manifests and Helm charts  
- 📝 Notes, best practices, and gotchas  
- 🔬 Mini-projects and experiments  

My goal with this repo is to deepen my understanding of cloud-native architecture and build a solid foundation for managing scalable, resilient applications in production environments.

Feedback, suggestions, and collaboration are always welcome!

## kubernetes beginner commands for pods, namespace, & deployment

This guide covers essential Kubernetes commands focused on managing pods, designed specifically for beginners. It provides straightforward explanations and examples to help you create, inspect, debug, and manage pods effectively in your Kubernetes cluster.

## 1. View All Nodes in the Cluster

`kubectl get nodes`

Functionality:
Displays a list of all nodes (machines or servers) in the Kubernetes cluster. It includes details such as node name, status, role (e.g., master/worker), and the Kubernetes version running on each node.

## 2. Create a New Pod

`kubectl run <pod-name> --image=<image-name>:<version>`

Example:
`kubectl run myfirstpod --image=ubuntu:latest`

Functionality:
Creates a new pod named myfirstpod using the specified Docker image (ubuntu:latest). The container will be based on this image and run inside the newly created pod.

## 3. Display All Pods

`kubectl get pods`

Functionality:
Lists all pods in the current namespace along with their status (e.g., Running, Pending, CrashLoopBackOff).

## 4. Display Pods with Additional Information

`kubectl get pods -o wide`

Functionality:
Displays all pods with extra details such as the node they’re running on, their IP addresses, and the container image used.

## 5. Get Detailed Information About a Pod

`kubectl describe pod <pod-name>`

Functionality:
Shows detailed information about a specific pod, including events, environment variables, volume mounts, restart count, and more. Useful for debugging.

## 6. Delete a Pod

`kubectl delete pod <pod-name>`

Example:

`kubectl delete pod myfirstpod`

Functionality:
Deletes the specified pod from the cluster. Useful for removing a pod that is crashing or no longer needed.

## 7. View Logs from a Pod

`kubectl logs <pod-name>`

Example: 
kubectl logs pod2

Functionality:
Displays the logs (standard output and standard error) of the main container in the specified pod. Helps in understanding what the application inside the pod is doing or why it's failing.

## 8. Access the Shell Inside a Pod

`kubectl exec -it <pod-name> -- /bin/bash`

Functionality:
Starts an interactive shell session inside the pod’s container. Useful for manual inspection, running commands, or debugging from inside the container. Use /bin/sh if /bin/bash is not available.

## 9. Test Pod Connectivity

`curl <pod-IP>:80`

Functionality:
Sends an HTTP request to port 80 of the given pod IP. This is useful for testing whether the service or application running inside the pod is reachable and responding correctly.

---

# Kubernetes Namespace Commands for Beginners

This document contains essential Kubernetes commands focused on managing namespaces and namespace-scoped resources. It is designed specifically for beginners to help you understand how to organize, isolate, and manage workloads within different namespaces in a Kubernetes cluster. Each command includes a simple explanation and examples to get you started quickly.

## 10. View All Namespaces in the Cluster

`kubectl get namespace`

**Functionality:**  
Displays all namespaces in the Kubernetes cluster. Namespaces help organize cluster resources into separate virtual clusters within the same physical cluster.

*Note:* Namespaces are virtual partitions within the same physical Kubernetes cluster.

---

## 11. View All Pods in a Specific Namespace

`kubectl get pods --namespace <namespace>`

**Functionality:**  
Displays all pods running within the specified namespace. This helps you focus on resources isolated to that particular namespace instead of the entire cluster.

---

## 12. Display Running Pods with Additional Details in a Specific Namespace

`kubectl get pods -o wide --namespace <namespace>`

**Functionality:**  
Displays all running pods within the specified namespace along with extra details such as the node they’re running on, pod IP addresses, and the container image used. This provides more context than the default pod listing.

---

## 13. Create a New Namespace

`kubectl create namespace <namespace>`

**Functionality:**  
Creates a new virtual namespace within the physical Kubernetes cluster. This namespace can then be used to organize and isolate resources such as pods, services, and deployments.

---

## 14. Deploy a Pod Within a Specific Namespace

`kubectl run dev-pod1 --image=nginx:latest --namespace <namespace>`

**Example:**  
`kubectl run dev-pod1 --image=nginx:latest --namespace development`

**Functionality:**  
Creates a new pod named `dev-pod1` using the `nginx:latest` image inside the specified namespace (`development` in the example). This helps you organize and isolate workloads within that namespace.

------------

## 15. Create a Deployment in the Kubernetes Cluster

`kubectl create deployment <deployment-name> --image=<image-name> --replicas=n`

Example:
`kubectl create deployment mysampleapp --image=nginx:latest --replicas=10`

Functionality:
Creates a new deployment in the Kubernetes cluster with the specified name, container image, and number of pod replicas. Deployments manage the lifecycle of pods, support rolling updates, and ensure the desired state is maintained.

💡 Note: You must specify the --image parameter; otherwise, the command will fail.

## 16. Create a Deployment Within a Specific Namespace

`kubectl create deployment <deployment-name> --image=<image-name> --replicas=<number> --namespace <namespace>`

Example:

`kubectl create deployment mysample --image=nginx:latest --replicas=10 --namespace development`

Functionality:
Creates a deployment named mysample using the nginx:latest image with 10 replicas inside the development namespace. This allows you to manage and isolate your deployment within that specific virtual partition of the Kubernetes cluster.

## 17. To display the deployment within a specific namespace

`kubectl get deployment --namespace <namespace-name>`

Example:
`kubectl get deployment --namespace development`

Functionality:
Displays all deployments running within the specified namespace (e.g., development). This helps you monitor and manage deployments that are logically separated within the Kubernetes cluster.

## 18. To display the pods within a specific namespace

`kubectl get pods --namespace <namespace-name>`

Example:
`kubectl get pods --namespace development`

Functionality:
Displays all running pods within the specified namespace (development in this case). This is useful for checking the status and health of pods isolated to a specific part of your Kubernetes cluster.

## Deployment commands

## 19. Update the Image Used by a Deployment

`kubectl set image deployment/<deployment-name> <container-name>=<image-name>:<tag>`

Example:
`kubectl set image deployment/test2 nginx=nginx:latest`

Functionality:
This command updates the container image used by a deployment. In this example, it sets the image for the container named nginx in the deployment test2 to nginx:latest.

✅ Note:

The container name (nginx in this case) must match the container defined in the deployment spec.

This command triggers a rolling update by default.

## 20. Check the Rollout Status of a Deployment

`kubectl rollout status deployment/<deployment-name>`

Example:
`kubectl rollout status deployment/mydeployment`

Functionality:
This command shows the status of the rollout for the specified deployment. It helps you monitor whether a new deployment or image update has completed successfully or is still in progress.

✅ Tip: Use this after changing the image or updating deployment configurations to ensure the update rolled out properly.

## 21. To undo a rollout use the command

`kubectl rollout undo deployment <deployment-name>`

Example:
`kubectl rollout undo deployment test2`

Functionality:
Reverts the deployment to the previous version in case the current rollout caused issues. Useful for quick rollback if something goes wrong after updating the deployment.

## 22. To check rollout history

`kubectl rollout history deployment <deployment-name>`

Example:

`kubectl rollout history deployment test2`

Functionality:
Displays the revision history of a Kubernetes deployment. This allows you to view previous versions of the deployment and track changes over time.

## 23. To go back to a specific version

`kubectl rollout undo deployment/<deployment-name> --to-revision=<revision-number>`

Example:
`kubectl rollout undo deployment/test --to-revision=2`

Functionality:
This command is used to rollout undo to a specific version of the image

## 24. View All ReplicaSets in the Cluster

`kubectl get replicaset`

Functionality:
Displays all the ReplicaSets (RS) in the current namespace. A ReplicaSet ensures that a specified number of pod replicas are running at any given time.

## 25. To scale a current deployment

`kubectl scale deployment <deployment-name> --replicas=<n>`

Example: 
`kubectl scale deployment test --replicas=15`

Functionality:
This command is used to scale a deployment by increasing or decreasing the number of pod replicas.

Labels:
labels are also a Kubernetes resource, but they are not standalone resources like pods or deployments.

## 26. To delete an existing deployment

`kubectl delete deployment <deployment-name>`

Example:
`kubectl delete deployment test2`

Functionality:
Functionality:
This command deletes the specified deployment from the Kubernetes cluster. Deleting a deployment also removes the associated ReplicaSets and the pods that it manages.

## 27. To Add or Modify a Label on a Pod

`kubectl label pods <pod-name> <key>=<value>`

Example:
`kubectl label pods mypod user=abhishek`

Functionality:
This command adds a label with the key user and value abhishek to the specified pod.

## 28. To display the labelled pods

`kubectl get pods --show-labels`

Functionality:
This command is used to display the labelled pods

## 29. To retrieve the pods with a specific label

`kubectl get pods -l <key>=<value>`

Example:
`kubectl get pods -l user=abhishek`

Functionality:
This command is used to display all the pods with this label

## 30. To view the deployment with a specific label

`kubectl get deployment -l <key>=<value>`

Example:
`kubectl get deployment -l user=abhishek`

Functionality:
This command is used to display the deployment with a specific label user=abhishek
