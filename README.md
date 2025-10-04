
***

# Kubernetes Install Scripts & Configurations

This repository provides scripts, configurations, and manifests to help you set up and manage Kubernetes clusters using different tools — **kind**, **kubeadm**, and **minikube** — plus **ingress** setup examples for routing and services.

***

## 📁 Directory Structure

| Directory | Description |
|------------|--------------|
| `kind/` | Scripts and configs to deploy Kubernetes using **kind** (Kubernetes in Docker) |
| `kubeadm/` | Manifests and installation scripts for **kubeadm**-based clusters |
| `minikube/` | Configuration files and examples for **minikube** local clusters |
| `ingress/` | Ingress controller manifests, rules, and example workload setups |

***

## 🛠 Prerequisites

Before starting, ensure you have the following:

- **Minimum system requirements:** 2 CPU cores, 2 GB RAM (4 GB recommended)  
- **Tools installed:**  
  - Docker (for kind and some kubeadm setups)  
  - kubectl (CLI tool to manage Kubernetes)  
- **For kubeadm setups:**  
  - Swap disabled (`swapoff -a`)  
  - Proper hostnames and networking configured  
  - SSH access between nodes (for multi-node setup)  
  - Container runtime (e.g. containerd, CRI-O) installed  

***

## 🚀 Getting Started

Follow the setup method that fits your environment.

### Using kind (Kubernetes in Docker)

1. Navigate into the directory:
   ```bash
   cd kind
   ```
2. Create a cluster using your config:
   ```bash
   kind create cluster --config kind-config.yaml
   ```

### Using kubeadm (for VM or bare-metal)

1. Go to your kubeadm setup directory:
   ```bash
   cd kubeadm
   ```
2. Initialize the control plane:
   ```bash
   kubeadm init --config kubeadm-config.yaml
   ```
3. Set up a networking plugin (example: Calico):
   ```bash
   kubectl apply -f calico.yaml
   ```

### Using minikube (lightweight local setup)

1. Enter the minikube directory:
   ```bash
   cd minikube
   ```
2. Start a local cluster with your preferred driver:
   ```bash
   minikube start --driver=<driver-name>
   ```

***

## 🌐 Ingress Setup

1. Go into the ingress directory:
   ```bash
   cd ingress
   ```
2. Apply ingress controller and ingress rule manifests:
   ```bash
   kubectl apply -f ingress-controller.yaml
   kubectl apply -f ingress-rules.yaml
   ```
3. Verify ingress resources:
   ```bash
   kubectl get ingress -A
   ```

***

## 🧩 Example Workflow

A typical local workflow could look like this:

1. Use **kind** to spin up a quick test cluster.  
2. Deploy ingress controller and example rules from the `ingress/` folder.  
3. Experiment with **kubeadm** on VMs for production-like environments.  
4. Use **minikube** for local application development and testing.

***

## 🛡 Troubleshooting & Tips

- Ensure ports **80** and **443** are open when using ingress.  
- Verify Docker is running before starting `kind` clusters.  
- Match **kubectl**, **kubeadm**, and **kubelet** versions for kubeadm setups.  
- Check cluster status:
  ```bash
  kubectl get nodes
  kubectl get pods -A
  ```
- Inspect issues using:
  ```bash
  kubectl describe <resource> <name>
  kubectl logs <pod-name>
  ```

***

