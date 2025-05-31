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
