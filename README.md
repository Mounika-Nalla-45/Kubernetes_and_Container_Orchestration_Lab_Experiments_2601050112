# Kubernetes and Container Orchestration – Lab Experiments

## Overview
This repository contains my Kubernetes lab experiments. It covers cluster creation, application deployment, Kubernetes internal components, and custom controller development.

---

## Experiment 1: Multi-Node Kubernetes Cluster Using Kind

**Aim:** To create a 3-node Kubernetes cluster, identify control-plane components, deploy an application, and test scaling and self-healing.

**What We Did:**
- Checked Docker Desktop, Kind, and kubectl.
- Created a 3-node cluster with 1 control-plane node and 2 worker nodes.
- Identified Kubernetes control-plane components.
- Deployed Nginx with 3 replicas.
- Deleted a Pod and observed automatic self-healing.
- Scaled the Deployment from 3 to 5 and then 2 replicas.
- Exposed the application using a Service.
- Accessed the Nginx application through localhost:8080.

**Concepts Learned:** Cluster, Nodes, Pods, Deployments, Control Plane, Services, Scaling, and Self-healing.

---

## Experiment 2: Trace kubectl Create Deployment End to End

**Aim:** To understand how Kubernetes components work together when a Deployment is created.

**What We Did:**
- Created an Nginx Deployment with 2 replicas.
- Used kubectl verbose mode to observe HTTP requests sent to the API Server.
- Examined Kubernetes events and their source components.
- Traced the ownership chain: Deployment → ReplicaSet → Pods.
- Inspected Kubernetes objects stored in etcd.
- Used crictl to inspect Pod sandboxes and containers.
- Examined Pod IP addresses and kubelet logs.
- Created a Service and inspected EndpointSlices and kube-proxy networking rules.
- Tested a 409 Conflict using an outdated YAML file and resourceVersion.

**Concepts Learned:** API Server, etcd, Controllers, Scheduler, kubelet, Container Runtime, Service Networking, Events, and Resource Version Conflict.

---

## Experiment 3: Write Your First Kubernetes Controller

**Aim:** To develop a custom Kubernetes controller using Go and client-go.

**What We Did:**
- Installed Go and configured the Windows PATH environment variable.
- Created a Go project using `go mod init`.
- Added the controller program (main.go).
- Installed Kubernetes client-go libraries.
- Used `go mod tidy` to manage dependencies.
- Ran the controller using `go run .`.
- Created a namespace named team-a.
- Added the label `klu.edu/managed=true`.
- Used Informer, Work Queue, and Reconcile to monitor namespaces.
- Automatically created a ConfigMap named welcome in labelled namespaces.
- Studied self-healing, catching up, running two controllers, and removing the label.

**Concepts Learned:** Go, client-go, Custom Controllers, Desired State, Actual State, Informer, Work Queue, Reconciliation, Namespace, and ConfigMap.

---
