# Kubernetes Intro to Advanced Workshop

I'll be doing a Kubernetes Intro to Advanced workshop on Feb 20th 9am to 5pm and Feb 25th 9am to 5pm.

Here is a rough syllabus for the workshop (subject to change):

## Overview (How we got here): [20 min]

- Story of a web dude (how a monolith service is managed) 
- Move from monolith to microservices
- How is the infrastructure moving with this trend (baremetal -> VM -> containers -> serverless) 
- Where everything is at on the technology curve
- What are containers? And what business problem do they solve?
    - Briefly explain namespaces
- What is k8s? What business problem does it solve?
    - operational cost (resource utilization)
- Some k8s adoption numbers, how fast it’s growing, adoption
 
## Cloud Native Ecosystem Landscape: [10 min]

- Explain all the names in the industry:
- *aaS layers (explain the different XaaS layers and where do containers/k8s fit in)
- **Container runtime**: docker, rkt, CRI-O, CRI-containerd, ... 
- **Orchestrators**: K8s, Mesos, Swarm, OpenShift, Rancher, ...
- **CNI**: Calico, Weave, Flannel, Romana, ...
- **Servicemesh**: istio, callium, nginmesh, hashicorp consul, ...
- **Managed k8s (K8SaaS)**: GKE, EKS, AKS, VNX (VMware), PCS, DigitalOcean, ...

## Conatinars: from 0 to 60: [20 min]

- Containers vs VMs
- Containers vs Processes
- How are containers made
- Chroot on steroids
- Terminology: Dockerfile, image, tag, container,layers
- Live "code to prod" demo: 
         Code -> Binary -> Dockerfile -> local container image -> image on DockerHub -> image on another machine -> image deployed in the cloud


## K8s core concepts: [30 min]

- Pods 
- Namespaces
- Labels/Selectors
- Service
- Deployment (ReplicaSets)
- Kubernetes YAML (API format)


## Lab 1: Basics [45 min]

- Deploy a simple nginx service (deployment, service)
- Scale it up/down 
- Create a service (expose it to the internet using GCP external Load Balancer)
- Look at pod logs, audit logs
- Do a rolling update
- Configure Horizontal Autoscaler
- GKE Kubernetes UI
- Basic `kubectl` CLI operations


## Day in a life of a container native app (CI/CD) [30 min]

- Typical workflow from developer's laptop (code) to production
- Dev tools
- Testing/QA
- CI tools
- CD workflow
- Production cluster management, A/B testing, upgrades, etc. 
 
## Advanced K8s concepts & security [45 min]

- ConfigMap
- DaemonSet
- StatefulSet
- Jobs
- Autoscaling
- Ingress 

---
- K8s security concepts 
- RBAC
- NetworkPolicy 
- Secrets
- Security in k8s context: [15 min]
    - Some of the concepts from https://kubernetes.io/blog/2018/07/18/11-ways-not-to-get-hacked/
- Easy ways to secure a k8s cluster
- (optional) k8s security landscape: companies (?)



## Lab 2: Security [60 min]

- Deploy a 2 service app
- Create NetworkPolicies to “secure” the network using Calico
- (Maybe) demo helmsploit (exploit that lets you bring down k8s network even with NetworkPolicies in place
- Create RBAC rules 
- Create a PodSecurityPolicy to disallow running a privileged pod
- "PlayTime" - try to break/bypass these security implementations 

 
## K8s architecture: [60 min]

- Day in a life of a packet
    - Same pod
    - Different pods, same host
    - Different pods, different host
    - Pod to service IP
    - Pod to service name
    - Pod to outside world
    - Outside world to pod
    
- Networking/CNI overview

Architecture:
- Control Plane
    - API server (components)
    - Networking CP (istio)
    - etcd
- “Data” Plane
    - kubelet
    - docker/CRI
    - Networking DP (CNI, Envoy)

- Brief overview of istio
 
 Developer advanced:
- Maybe try to access etcd to see how the data/objects are stored in it
- Create some Custom Resource Definition schema, and create CRD objects under it
- Look at etcd to see how our custom resource is stored  

## (take home) Lab 3: Advanced use (istio) [60 min]

Could be a take home lab
- Deploy istio on kubernetes
- Deploy the istio guestbook app
- Create istio policies, monitoring, request routing, tracing, service graph, visualization


## Closing

- Kubernetes deployers
- Kubernetes learning resources
- Free clusters
- Future courses
