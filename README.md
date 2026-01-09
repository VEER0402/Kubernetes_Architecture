🚀 What is Kubernetes?


Kubernetes (K8s) is a container orchestration system.

In simple words:

A system that runs your containers automatically, heals them, scales them, and distributes traffic.

Kubernetes works on a cluster, which means:

A group of machines working together as ONE system.

These machines are divided into two parts:

Control Plane (Brain)

Worker Nodes (Hands that do the work)

============================================================================================
==========================================================================================


🧠 Kubernetes Architecture

Below is the simplest and clearest text‑based diagram that explains everything.


<img width="1024" height="1024" alt="k8sarchitecture" src="https://github.com/user-attachments/assets/b13554eb-3bfe-4caa-afd6-ea5d3e16aed3" />




✅ Kubernetes Components — Explained in Human Language

🔵 DATA PLANE (Worker Nodes)

These machines run your actual application.

1️⃣ Container Runtime (Docker / containerd)

Runs your containers.

Real-life example:

Jaise restaurant me chef actual food banata hai, waise container runtime actual container run karta hai.




2️⃣ Kubelet

Node ka manager.

API Server se instruction leta hai: "3 pods chalao"

Runtime ko bolta hai container start karo

Pod gir jaye to fir se start kar deta hai

Real-life example:

Aapka payment service crash ho gaya → kubelet automatically naya pod chala dega.





3️⃣ kube-proxy

Networking + load balancing.

Iptables/IPVS rules banata hai traffic forwarding ke liye

Service se pod tak traffic bhejta hai

Real-life example:

Agar 3 pods chal rahe hain, kube-proxy traffic ko equally baant dega.

🔴 CONTROL PLANE (Master / Brain)

Ye decide karta hai ki cluster kaise chalega.




1️⃣ API Server — Heart of Kubernetes

Sab commands (kubectl, UI, CI/CD) yahin se pass hoti hain.

Real-life example:

Aap order dete ho → "3 pizzas chahiye" → Manager (API Server) request register karta hai.



2️⃣ Scheduler

Decides which node will run the pod.

Real-life example:

Jaise restaurant me manager decide karta hai ki kaun sa chef kaam karega.



3️⃣ etcd

Kubernetes ka database.

Stores:

Pods

Nodes

Deployments

Configs

Cluster state

Real-life example:

Restaurant ka master notebook jisme sab orders likhe hote hain.




4️⃣ Controller Manager

Self-healing.

Pod mar gaya → naya banata hai

Desired replicas = actual replicas maintain karta hai

Real-life example:

Aapne 3 waiters decide kiye → ek chala gaya → manager instantly replacement bhej deta hai.




5️⃣ Cloud Controller Manager (CCM)

Cloud specific kaam karta hai (AWS, Azure, GCP):

Load balancer banana

Disk attach karna

Node health manage karna

Real-life example:

Cloud bolta hai: "LoadBalancer service? Ok, main AWS ELB create kar deta hoon."




🧩 Real-Life Example (Very Easy)

Consider your company has two microservices:

users-service

payments-service

You deploy:

replicas: 3

Flow:

kubectl apply → API Server ko request jati hai

API Server → etcd me store

Controller: "3 pods chahiye"

Scheduler nodes choose karta hai

kubelet pods banata hai

Runtime containers run karta hai

kube-proxy traffic load-balance karta hai

If 1 pod crashes → automatically recreate

This is Kubernetes power:

Self healing

Scaling

High availability

Automated deployments
