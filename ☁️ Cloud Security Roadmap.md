# Comprehensive Cloud Security Roadmap — Compiled Edition
### Linux → Containers → Orchestration → Kubernetes → Kubernetes Security → Cloud Security → Cloud Platforms

# Roadmap structure

```text
PART I   Linux foundations + Linux security
PART II  Networking
PART III Containers + isolation + sandboxes
PART IV   Linux → Kubernetes
PART V    Kubernetes fundamentals + orchestration
PART VI   Kubernetes hands-on labs
PART VII  Kubernetes security
PART VIII Kubernetes offensive security + certification
PART IX   Local security lab + practical projects
PART X    Cloud fundamentals
PART XI   Cloud providers + IAM + networking
PART XII  Managed Kubernetes in the cloud
PART XIII Cloud IaC / DevSecOps / assessment
PART XIV Cloud offensive security
PART XV  Cloud detection / IR
```

The principle is:

> **Master the operating system → understand containers → understand orchestration → secure Kubernetes → then move the same security concepts into public cloud.**

---

# 0. How to use this roadmap
## TL;DR: do this
> **Linux Hackathon → From Server to Cluster → K8s Hackathon → KubernetesLabs → KubeKosh (optional)  → THM / Killercoda → Kubernetes Goat → yandex cloud courses → kube-bench/Kubescape/Trivy/Kyverno/Falco → EKS/AKS/GKE → CloudGoat**

```text
                    CLOUD SECURITY

                         │
                         ▼
              ┌───────────────────┐
              │ Linux Hackathon   │
              └─────────┬─────────┘
                        │
                        ▼
              From Server to Cluster
                        │
                        ▼
                K8s Hackathon
                        │
              ┌─────────┴─────────┐
              ▼                   ▼
       KubernetesLabs          KubeKosh (optional)
              │                   │
              └─────────┬─────────┘
                        ▼
           Killercoda / TryHackMe labs
                        │
                        ▼
                 Kubernetes Core
                        │
        ┌───────────────┼────────────────┐
        │               │                │
        ▼               ▼                ▼
      Helm            ArgoCD          Networking
        │               │                │
        └───────────────┼────────────────┘
                        ▼
                 Kubernetes Security
                        │
        ┌───────────────┼────────────────┐
        │               │                │
       RBAC        Pod Security     NetworkPolicy
        │               │                │
        └───────────────┼────────────────┘
                        ▼
                 CKS Preparation
                        │
        ┌───────────────┼────────────────┐
        ▼               ▼                ▼
    kube-bench       Kubescape          Trivy
        │               │                │
        └───────────────┼────────────────┘
                        ▼
                 Kyverno + Falco
                        │
                        ▼
              Kubernetes Goat
                        │
                        ▼
                  K8s attack paths
                        │
                        ▼
               Yandex courses + AWS / Azure / GCP (optinal) 
                        │
                        ▼
             Cloud IAM + Networking
                        │
                        ▼
                    EKS / AKS / GKE
                        │
                        ▼
               Terraform + GitOps
                        │
                        ▼
                 CloudGoat / Prowler
                        │
                        ▼
              Cloud Detection + IR
                        │
                        ▼
             Cloud Security Engineer
```





The practical progression is:

```text
Linux
  │
  ├── Linux administration
  ├── Linux networking
  ├── Linux security
  ├── Linux hardening
  └── Linux internals
          │
          ▼
Networking
  │
  ├── TCP/IP
  ├── DNS
  ├── routing
  ├── firewalls
  ├── TLS
  └── VPN
          │
          ▼
Cloud Fundamentals
  │
  ├── AWS
  ├── Azure
  ├── GCP
  ├── IAM
  ├── VPC/VNet
  ├── storage
  ├── compute
  └── cloud APIs
          │
          ▼
Containers
  │
  ├── Docker
  ├── OCI
  ├── namespaces
  ├── cgroups
  ├── capabilities
  ├── seccomp
  └── container security
          │
          ▼
Kubernetes
  │
  ├── Architecture
  ├── kubectl
  ├── workloads
  ├── networking
  ├── storage
  ├── scheduling
  ├── Helm
  └── troubleshooting
          │
          ▼
Kubernetes Security
  │
  ├── Authentication
  ├── RBAC
  ├── ServiceAccounts
  ├── Secrets
  ├── NetworkPolicy
  ├── Pod Security
  ├── Admission
  ├── seccomp
  ├── AppArmor
  ├── Falco
  ├── Kyverno
  └── audit logging
          │
          ▼
Cloud-Native Security
  │
  ├── EKS / AKS / GKE
  ├── Workload Identity
  ├── Cloud IAM
  ├── IaC
  ├── GitOps
  ├── supply chain
  └── DevSecOps
          │
          ▼
Cloud Security
  │
  ├── Cloud detection
  ├── Cloud IR
  ├── attack paths
  ├── cloud pentesting
  └── security architecture
```
---

# 1. Linux foundations, Linux security and hardening

## 1.1 Linux fundamentals

Before going deep into cloud/Kubernetes security, make Linux second nature.

### Files

```text
/etc
/var
/proc
/sys
/dev
/run
/tmp
```

### Processes

```bash
ps
top
htop
pstree
pgrep
lsof
strace
```

### Permissions

```bash
chmod
chown
chgrp
umask
sudo
```

Understand:

```text
UID
GID
SUID
SGID
sticky bit
ACLs
capabilities
```

### Services

```bash
systemctl
journalctl
systemd
```

### Networking

```bash
ip
ss
tcpdump
dig
curl
nc
iptables
nft
```

## 1.2 Linux hardening

Cloud security starts with the Linux OS. Hardening means reducing the attack surface through software minimization and strict permissions.

Study:

- RWX permissions
- ACLs
- least privilege
- sticky bit, especially `/tmp`
- `sudo` configuration
- `/etc/sudoers`
- service hardening
- firewalling
- logging and auditing
- systemd
- cron
- process/resource limits
- Linux capabilities
- AppArmor / SELinux

The CbS roadmap specifically calls out incorrect [`/etc/sudoers` ](https://www.digitalocean.com/community/tutorials/how-to-edit-the-sudoers-file)configuration as a critical risk and uses CVE-2019-14287 as an example of UID-handling problems. It also recommends modern hardening such as restricting sudo behavior, `requiretty` where applicable to the target environment, and mandatory auditing.

## 1.3 Free hands-on Linux practice

### ⭐ Linux Hackathon

- [ ] https://linuxhackathon.com/

Use it as the main practical Linux foundation.

Important challenges for cloud security:

```text
05  File permissions
06  Processes
07  Users/groups
08  Bash scripting
12  Webserver
13  Server hardening
14  Containers
15  Networking
16  systemd
18  Cron
19  Firewall
20  Troubleshooting
```

The particularly useful progression is:

```text
Linux Hackathon
      ↓
From Server to Cluster
      ↓
K8s Hackathon
```

### TryHackMe — Linux Fundamentals

- [ ] https://tryhackme.com/module/linux-fundamentals

Practice:

- `chmod`
- `chown`
- Linux system structure

### TryHackMe — Agent Sudo

- [ ] https://tryhackme.com/room/agentsudoctf

Focus:

- sudo configuration
- privilege escalation
- securing sudo

### SadServers — La Rinconada

- [ ] https://sadservers.com/scenarios

Practice a live challenge involving sudo/root access.

### SadServers — Taipei

- [ ] https://sadservers.com/scenario/taipei

Focus:

- firewall configuration
- port knocking

### SadServers — Saint John

- [ ] https://sadservers.com/scenarios

Focus:

- identifying a process consuming disk space with logs
- understanding a potential DoS/resource-exhaustion risk

### SadServers — Bilbao

- [ ] https://sadservers.com/scenarios

Focus:

- fixing a Kubernetes pod manifest that will not start

---

# 2. Networking for cloud and Kubernetes security

Build networking knowledge before treating cloud networking as a collection of provider-specific buttons.

## 2.1 Core networking

Learn:

```text
TCP/IP
DNS
routing
subnets
CIDR
ARP
NAT
firewalls
TLS
VPN
http/HTTPS
load balancing
reverse proxies
```

Linux tools:

```bash
ip
ss
tcpdump
dig
curl
nc
iptables
nft
```

## 2.2 Kubernetes networking

Learn:

```text
CNI
DNS
Service discovery
ClusterIP
NodePort
LoadBalancer
Ingress
Gateway API
NetworkPolicy
pod-to-pod traffic
service-to-service traffic
```

Important mental model:

```text
Pod
 ↓
CNI
 ↓
Network namespace
 ↓
Node networking
 ↓
Kubernetes Service
 ↓
Ingress / Gateway
 ↓
Cloud load balancer
```

## 2.3 Security model

The CbS roadmap emphasizes that Kubernetes pods can communicate broadly by default and that a Zero Trust approach requires NetworkPolicies to constrain traffic.

Practice:

- default-deny policies
- namespace isolation
- ingress/egress rules
- service-to-service allowlists
- DNS considerations
- CNI security
- Cilium / Calico
- cloud security groups
- cloud VPC/VNet controls

### Killercoda — NetworkPolicy

- [ ] https://killercoda.com/killer-shell-cks/scenario/networkpolicy-create-default-deny

Practice creating a default-deny NetworkPolicy.

### KubernetesLabs

- [ ] https://nirgeier.github.io/KubernetesLabs/Tasks/

Use the networking, service-discovery, Ingress and Gateway API exercises.

---

# 7. Containers and container security

Do not jump directly from Kubernetes basics to CKS.

## 7.1 Container architecture

Understand:

```text
Pod
 ↓
container
 ↓
container runtime
 ↓
Linux namespaces / cgroups
 ↓
Linux kernel
```

Learn:

```text
Docker
OCI
containerd
runc
namespaces
cgroups
capabilities
seccomp
AppArmor
SELinux
rootless containers
```

## 7.2 Namespaces

Study:

```text
PID
NET
MNT
USER
IPC
UTS
```

Namespaces provide the isolation/virtualization layer that makes processes believe they have their own environment.

## 7.3 Cgroups

Learn:

```text
CPU limits
memory limits
PID limits
resource accounting
DoS protection
fork bombs
```

## 7.4 Capabilities

Understand why Linux capabilities split traditional root privileges.

Examples:

```text
CAP_NET_BIND_SERVICE
CAP_SYS_ADMIN
```

Treat `CAP_SYS_ADMIN` as especially important when studying container escape and privilege escalation.

## 7.5 Seccomp

Understand:

- system-call filtering
- reducing kernel attack surface
- default vs custom profiles

## 7.6 Container hardening

Practice:

```text
runAsNonRoot
readOnlyRootFilesystem
drop capabilities
seccomp
AppArmor
resource limits
non-root images
minimal images
rootless containers
image scanning
```

### TryHackMe — Container Hardening

- [ ] https://tryhackme.com/room/containerhardening

The supplied roadmap marks this as **PAID** and explicitly says to find an equivalent. Therefore it should not be treated as a required free lab.

### Namespaces & Cgroups — Simple Sandbox

- [ ] https://github.com/TamimEhsan/Simple-Sandbox

Practice manual container/sandbox creation with `unshare`.

### Kubernetes/container introduction video

- [ ] https://youtu.be/TlHvYWVUZyc?si=rqzJ7KCWdv6YYiPZ

A brief Kubernetes/container introduction from the CbS roadmap.

---

# 8. Advanced sandboxes: gVisor and MicroVMs (optional)

Standard containers share the host kernel and are therefore not equivalent to a VM security boundary.

## gVisor

Learn:

```text
container
 ↓
gVisor
 ↓
host kernel
```

gVisor intercepts userspace system calls and provides an additional isolation boundary.

### Killercoda — gVisor

- [ ] https://killercoda.com/killer-shell-cks/scenario/sandbox-gvisor

Practice launching isolated Kubernetes Pods with gVisor.

## MicroVMs

Study:

```text
Kata Containers
Firecracker
```

The CbS roadmap frames MicroVMs as running workloads in lightweight VMs with their own kernel, providing stronger hardware/kernel isolation.

---

# 9. Linux → Kubernetes bridge

## ⭐ From Server to Cluster

- [ ] https://fromservertocluster.com/

A 15-chapter practical bridge between Linux and Kubernetes.

Focus:

```text
Linux
  ├── processes
  ├── networking
  ├── namespaces
  ├── services
  └── containers
        ↓
    Kubernetes
```

This prevents Kubernetes from becoming a collection of YAML commands disconnected from Linux internals.

---

# 10. Kubernetes fundamentals

Learn the architecture first.

## 10.1 Cluster architecture

```text
Cluster
Node
Control Plane
API Server
etcd
Scheduler
Controller Manager
kubelet
kube-proxy
CRI
CNI
CSI
```

Understand the control flow:

```text
kubectl
  ↓
API Server
  ↓
etcd / controllers / scheduler
  ↓
kubelet
  ↓
container runtime
  ↓
Pod
```

## 10.2 Workloads

Learn:

```text
Pod
Deployment
ReplicaSet
DaemonSet
StatefulSet
Job
CronJob
```

## 10.3 Services and traffic

Learn:

```text
Service
Ingress
Gateway
ClusterIP
NodePort
LoadBalancer
```

## 10.4 Configuration

Learn:

```text
ConfigMap
Secret
Volume
PV
PVC
Namespace
```

## 10.5 Scheduling

Learn:

```text
scheduling
taints
tolerations
node affinity
pod affinity
pod anti-affinity
topology spread
```

---

# 11. ⭐ K8s Hackathon

- [ ] https://k8shackathon.com/

One of the highest-priority resources in this roadmap.

It contains progressive hands-on challenges covering CKA/CKAD/CKS-style material.

Important sequence:

```text
01 Containers
02 Pods
03 Kind cluster
04 Deployments
05 Services
06 Ingress / Gateway API
07 Storage
08 ConfigMaps / Secrets
09 RBAC / Security
10 Autoscaling
11 Helm / Kustomize
12 Observability
13 Troubleshooting
...
```

**Challenge 03 explicitly builds a local multi-node Kubernetes cluster using Kind.**

Coverage:

```text
CKA
├── cluster
├── nodes
├── networking
├── storage
├── scheduling
├── troubleshooting
└── administration

CKAD
├── applications
├── workloads
├── configuration
├── services
├── storage
└── observability

CKS
├── RBAC
├── Pod Security
├── NetworkPolicy
├── security contexts
├── runtime security
└── security hardening
```

---

# 12. ⭐ KubernetesLabs

- [ ] https://nirgeier.github.io/KubernetesLabs/Tasks/

Use it as a primary task-oriented Kubernetes course.

Core topics:

```text
Kubernetes CLI
Pod debugging
Deployments
Services
ConfigMaps
Secrets
Networking
Service discovery
Scheduling
Affinity
Anti-affinity
Taints
Tolerations
Topology spread
```

## Kubernetes ecosystem

```text
Helm
ArgoCD
Kubebuilder
KEDA
Harbor
Air-gapped Kubernetes
```

## Helm

Practice:

```text
chart creation
packaging
templating
repositories
deployment
best practices
```

Security:

```text
template injection
malicious charts
untrusted repositories
secrets in values
supply-chain attacks
```

## ArgoCD

Practice:

```text
CLI
application deployment
GitOps
App of Apps
sync waves
fleet management
```

Security:

```text
ArgoCD RBAC
repository credentials
secrets
application permissions
project restrictions
sync policies
image signing
admission policies
```

## Harbor

Study:

```text
image scanning
RBAC
signing
provenance
vulnerability scanning
registry access
```

The Harbor + ArgoCD Airgap tasks are particularly useful for:

```text
registry
ingress
GitOps
image mirroring
offline deployment
```

---

# 13. Other free Kubernetes practice

## k8sQuest

- [ ] https://github.com/Manoj-engineer/k8squest

CLI game for Kubernetes troubleshooting and basics.

## FastHack Kubernetes

- [ ] https://github.com/ricmmartins/fasthack-kubernetes

Use as an additional Kubernetes learning roadmap.

## KodeKloud — Game of Pods

- [ ] https://learn.kodekloud.com/user/courses/kubernetes-challenges

Use as an additional practical Kubernetes exercise source.

## Play with Kubernetes

- [ ] https://training.play-with-kubernetes.com/

Browser-based Kubernetes practice.

## iximiuz Labs

- [ ] https://labs.iximiuz.com

Useful for low-level/container/Kubernetes experimentation.

## Killercoda

- [ ] https://killercoda.com/

Use for disposable browser-based Linux/Kubernetes environments.

Search scenarios for:

```text
Kubernetes
CKA
CKS
RBAC
NetworkPolicy
security
Cilium
Falco
Helm
Ingress
troubleshooting
```

Recommended progression:

```text
Killer Shell CKA
      ↓
Kubernetes scenarios
      ↓
Killer Shell CKS
      ↓
security scenarios
```

## KubeKosh

- [ ] https://github.com/zeborg/kubekosh

Runs a real K3s cluster inside Docker with browser terminal + automated scenario validation.

Current scenario families listed in the source roadmap:

```text
Kubernetes Basics        40 scenarios
Gateway API              10
CKAD                     25
CKA                      40
CKS                      25
Istio                    10
Traefik                  10
HAProxy                  10
Falco                    10
```

CKS topics:

```text
Pod Security Admission
NetworkPolicy
seccomp
AppArmor
RBAC
```

## GIRUS

- [ ] https://girus.io/

Free/open-source interactive labs for:

```text
Kubernetes
Docker
AWS
Terraform
DevOps
```

Learning model:

```text
guided task
    ↓
interactive terminal
    ↓
real environment
    ↓
validation
```

## KubeLab

- [ ] https://github.com/natrontech/kubelab

Additional web-based interactive Kubernetes exercises.

## Kubernetes Practical Exercises

- [ ] https://github.com/seifrajhi/Kubernetes-practical-exercises-Hands-on

Practice with:

```text
kind
k3d
k3s
Docker Desktop
```

and use its networking exercises as additional hands-on work.

## Kubernetes learning path

- [ ] https://github.com/NotHarshhaa/kubernetes-learning-path

---

# 14. Kubernetes security architecture

Once Kubernetes fundamentals are comfortable, learn security as a set of control layers:

```text
Kubernetes
    │
    ├── Authentication
    │
    ├── Authorization
    │      └── RBAC
    │
    ├── Admission
    │      ├── PSS
    │      └── Kyverno
    │
    ├── Network
    │      └── NetworkPolicy
    │
    ├── Workload
    │      └── SecurityContext
    │
    ├── Runtime
    │      └── Falco
    │
    └── Audit
           └── Kubernetes audit logs
```

---

# 15. Kubernetes authentication

Learn:

```text
client certificates
ServiceAccount tokens
OIDC
cloud IAM
```

Cloud mappings:

```text
AWS IAM
   ↓
EKS
   ↓
Kubernetes identity
   ↓
RBAC
```

```text
Azure Entra ID
   ↓
AKS
```

```text
GCP IAM
   ↓
GKE
```

Understand both **human identities** and **workload identities**.

---

# 16. Kubernetes RBAC — make this one of your strongest skills

Learn every object:

```text
Role
ClusterRole
RoleBinding
ClusterRoleBinding
ServiceAccount
User
Group
Subject
Verb
Resource
API Group
```

Use:

```bash
kubectl auth can-i
```

Build:

```text
viewer
developer
namespace-admin
cluster-admin
```

Ask:

```text
Can viewer read Secrets?
Can developer create Pods?
Can developer create Roles?
Can developer create RoleBindings?
Can ServiceAccount access another namespace?
Can it create a privileged Pod?
```

## RBAC least privilege lab

- [ ] https://killercoda.com/killer-shell-cks/scenario/rbac-serviceaccount-permissions

Practice limiting ServiceAccount permissions.

## RBAC attack chain

```text
Compromised application
        ↓
Pod RCE
        ↓
ServiceAccount
        ↓
Token
        ↓
Kubernetes API
        ↓
RBAC enumeration
        ↓
Secrets
        ↓
Pod creation
        ↓
Privilege escalation
```

Then fix the same attack path with least privilege.

---

# 17. Kubernetes Pod Security

Learn:

```text
securityContext
runAsNonRoot
runAsUser
fsGroup
privileged
allowPrivilegeEscalation
capabilities
readOnlyRootFilesystem
seccomp
AppArmor
SELinux
Pod Security Admission
Pod Security Standards
```

Understand the relationship:

```text
Container hardening
        ↓
Pod security context
        ↓
Pod Security Admission
        ↓
Admission policy
```

---

# 18. NetworkPolicy and Zero Trust

Practice:

```text
default deny
namespace isolation
ingress allowlists
egress allowlists
DNS exceptions
service-to-service policies
```

Use:

- K8s Hackathon
- KubernetesLabs
- Killercoda
- Cilium labs

---

# 19. Admission control and Kyverno

## Kyverno

- [ ] https://github.com/kyverno/kyverno

Learn to enforce:

```text
No privileged containers
No root containers
No :latest
Approved registries only
Required labels
Required resource limits
Required NetworkPolicy
Signed images
```

Model:

```text
Developer
   ↓
kubectl apply
   ↓
Kyverno
   ├── compliant → allow
   └── violation → deny
```

---

# 20. Kubernetes security auditing and assessment

## kube-bench

- [ ] https://github.com/aquasecurity/kube-bench

Checks Kubernetes configuration against CIS Kubernetes Benchmark recommendations.

Workflow:

```text
Run kube-bench
      ↓
Findings
      ↓
Understand every finding
      ↓
Fix
      ↓
Run again
```

Do not simply paste the report into a README.

## Kubescape

- [ ] https://github.com/kubescape/kubescape

Use for:

```text
Kubernetes posture
CIS
NSA/CISA
misconfigurations
risk
compliance
```

Compare:

```text
kube-bench
    vs
Kubescape
```

Understand what each actually measures.

## Trivy

- [ ] https://github.com/aquasecurity/trivy

Use it across:

```text
Docker images
filesystem
Git repository
Kubernetes
Helm
Terraform
IaC
secrets
SBOM
vulnerabilities
```

Workflow:

```text
Build
 ↓
Trivy
 ↓
Fix
 ↓
Trivy
 ↓
Deploy
 ↓
Kubernetes
```

---

# 21. Kubernetes runtime security

## Falco

- [ ] https://github.com/falcosecurity/falco

Detect:

```text
shell spawned in container
unexpected process
sensitive file access
privilege escalation
unexpected network connection
container runtime abuse
```

Conceptual distinction:

```text
Trivy
  =
before runtime

Kyverno
  =
at admission

Falco
  =
during runtime
```

Learn:

```text
syscalls
eBPF
runtime events
Falco rules
detection
response
```

### Killercoda — Falco

- [ ] https://killercoda.com/killer-shell-cks/scenario/falco-change-rule

Practice live monitoring and changing Falco rules.

---

# 22. TryHackMe Kubernetes security

Use THM as **supplementary** Kubernetes security practice, not as the primary free Kubernetes curriculum, because the source roadmap notes that access status can vary and some relevant rooms/modules are Premium.

## Intro to Containerisation

- [ ] https://tryhackme.com/room/introtocontainerisation

## Cluster Hardening

- [ ] https://tryhackme.com/room/clusterhardening

Topics:

```text
cluster hardening
secure configuration
Kubernetes architecture
security considerations
```

## K8s Best Security Practices

- [ ] https://tryhackme.com/room/k8sbestsecuritypractices

Topics:

```text
ServiceAccounts
RBAC
Roles
RoleBindings
Kubernetes API
security best practices
```

Learning objectives include creating Roles/RoleBindings and understanding Kubernetes API requests.

## K8s Runtime Security

- [ ] https://tryhackme.com/room/k8sruntimesecurity

Topics:

```text
runtime attacks
privilege escalation
runtime security
Falco
Kubernetes runtime monitoring
```

## Kubernetes Hardening module

- [ ] https://tryhackme.com/module/kubernetes-hardening

The source roadmap lists:

```text
Cluster Hardening
K8s Best Security Practices
Microservices Architectures
K8s Runtime Security
Secure GitOps
```

## Kubernetes for You / Insekube

- [ ] https://tryhackme.com/room/kubernetesforyouly

- [ ] https://tryhackme.com/room/insekube

Use as additional Kubernetes security practice where available.

---

# 23. Kubernetes offensive security

## Kubernetes Goat

- [ ] https://github.com/madhuakula/kubernetes-goat

⭐⭐⭐⭐⭐ priority

Intentionally vulnerable Kubernetes cluster for hands-on exploitation.

Treat it as:

```text
Kubernetes security
       +
CTF
       +
attack simulation
```

Prerequisites:

```text
Kubernetes
RBAC
containers
networking
Linux
```

Practice:

```text
container compromise
RBAC abuse
secrets
ServiceAccounts
API attacks
privilege escalation
container escape
```

## Kube-Goat

- [ ] https://github.com/ksoclabs/kube-goat

Use after Kubernetes Goat as a second deliberately vulnerable Kubernetes environment.

Suggested progression:

```text
Kubernetes Goat
      ↓
Kube-Goat
```

---

# 24. Build your own Kubernetes attack chain

After Kubernetes Goat, build your own intentionally vulnerable environment.

Attack version:

```text
Web application
      ↓
RCE
      ↓
Container
      ↓
ServiceAccount
      ↓
Kubernetes API
      ↓
RBAC
      ↓
Secret
      ↓
Pod creation
      ↓
Privileged workload
      ↓
Node
```

Defensive version:

```text
NetworkPolicy
RBAC
PSS
seccomp
AppArmor
Kyverno
Falco
audit logs
```

This is one of the most important portfolio exercises in the roadmap.

---

# 25. Helm security

Helm is part of Kubernetes security because it is part of the deployment/supply chain.

Learn:

```text
Chart
values.yaml
templates
release
repository
dependencies
hooks
OCI registry
```

Security:

```text
template injection
malicious charts
untrusted repositories
secrets in values
supply-chain attacks
```

Secure pipeline:

```text
Helm
 ↓
Trivy
 ↓
Kyverno
 ↓
signed image
 ↓
deployment
```

Use the Helm tasks in KubernetesLabs extensively.

---

# 26. GitOps / ArgoCD security

Understand:

```text
Git
 ↓
ArgoCD
 ↓
Kubernetes
```

Attack chain:

```text
Git compromise
 ↓
malicious manifest
 ↓
ArgoCD
 ↓
cluster
```

Study:

```text
ArgoCD RBAC
repository credentials
secrets
application permissions
project restrictions
sync policies
image signing
admission policies
```

KubernetesLabs provides practical ArgoCD exercises including:

```text
App of Apps
sync waves
fleet management
```

---

# 27. Container registry / Harbor security

Architecture:

```text
Developer
    ↓
CI
    ↓
Image
    ↓
Harbor
    ↓
Kubernetes
```

Security controls:

```text
image scanning
RBAC
signing
provenance
vulnerability scanning
registry access
```

Use KubernetesLabs Harbor + ArgoCD/Airgap exercises.

---

# 28. Kubernetes security certification resources

## Isovalent CKS Study Guide

- [ ] https://github.com/isovalent/CKS-Study-Guide

Topics include:

```text
NetworkPolicy
Cilium
Pod-to-pod encryption
mTLS
microservice security
Cilium security
```

and links to hands-on labs.

## CKS Preparation Guide

- [ ] https://github.com/leandrocostam/cks-preparation-guide

Use as a study map around the current CKS curriculum and official Kubernetes documentation.

## CKS practice

- [ ] https://github.com/snigdhasambitak/cks

Includes material on:

```text
Contexts
Falco
API server security
```

and points to Killercoda CKA/CKS scenarios.

## ViktorUJ CKS/CKA/CKAD/EKS/AWS labs

- [ ] https://github.com/ViktorUJ/cks

Combines:

```text
CKA
CKS
CKAD
EKS
AWS
KCSA
KCNA
```

with automated lab creation/mock exams. Several labs require AWS infrastructure, so use this later rather than as a purely local course.

---

# 36. Security tooling laboratory

Build a local environment containing:

```text
                         K8S SECURITY LAB

                             Kubernetes
                                  │
            ┌─────────────────────┼─────────────────────┐
            │                     │                     │
           RBAC              NetworkPolicy         Pod Security
            │                     │                     │
            ▼                     ▼                     ▼
        kubectl             Cilium/Calico               PSS
                                  │
                                  │
                       ┌──────────┴──────────┐
                       │                     │
                    Kyverno                Trivy
                       │                     │
                       ▼                     ▼
                  Admission               Scanning
                                              │
                                              ▼
                                            Falco
                                              │
                                              ▼
                                      Runtime Security
```

---

# 37. Ultimate local lab

Eventually build:

```text
                          Linux
                            │
                          Docker
                            │
                    ┌───────┴───────┐
                    │               │
                   Kind            K3s
                    │
              Kubernetes
                    │
       ┌────────────┼────────────┐
       │            │            │
     Helm         ArgoCD       Cilium
       │            │            │
       └────────────┼────────────┘
                    │
                 Security
                    │
       ┌────────────┼─────────────┐
       │            │             │
    Kyverno       Trivy         Falco
       │            │             │
       └────────────┼─────────────┘
                    │
                Assessment
                    │
           ┌────────┴─────────┐
           │                  │
       kube-bench          Kubescape
```

Then add:

```text
Prometheus
Grafana
Loki
OpenTelemetry
Tempo
```

---

# 38. Cloud security projects

## Project 1 — Secure Linux server

Build:

```text
Ubuntu
SSH
users
sudo
auditd
firewall
Fail2Ban
AppArmor
logging
```

Then attack it using the Linux/SadServers/THM exercises.

## Project 2 — Secure Docker host

Build:

```text
Docker
Docker Bench
Trivy
rootless containers
capabilities
seccomp
AppArmor
```

## Project 3 — Secure Kubernetes cluster

Use:

```text
kind
RBAC
PSS
NetworkPolicy
Kyverno
Trivy
kube-bench
Kubescape
Falco
```

## Project 4 — Vulnerable Kubernetes cluster

Use:

```text
Kubernetes Goat
Kube-Goat
```

Attack:

```text
Pod
 ↓
ServiceAccount
 ↓
RBAC
 ↓
Secrets
 ↓
Node
```

## Project 5 — Secure GitOps platform

Build:

```text
GitHub
   ↓
CI
   ↓
Trivy
   ↓
SBOM
   ↓
Image signing
   ↓
Harbor
   ↓
ArgoCD
   ↓
Kyverno
   ↓
Kubernetes
```

## Project 6 — Cloud-native attack chain

Build:

```text
AWS
 │
 └── EKS
       │
       └── Pod
             │
             └── ServiceAccount
                    │
                    └── AWS IAM
                           │
                           └── S3
```

Document:

```text
attack
impact
detection
prevention
remediation
```

---

# 39. Main practical resource hierarchy

## Tier 1 — Main Kubernetes courses

1. **K8s Hackathon**
2. **KubernetesLabs**
3. **KubeKosh**
4. **GIRUS**
5. **Killercoda**

## Tier 2 — Kubernetes security

6. **Kubernetes Goat**
7. **Kube-Goat**
8. **KubeKosh CKS/Falco**
9. **TryHackMe Kubernetes security rooms**
10. **CKS Study Guides**

## Tier 3 — Security tools

11. **kube-bench**
12. **Kubescape**
13. **Trivy**
14. **Kyverno**
15. **Falco**
16. **Cilium**

## Tier 4 — Cloud

17. AWS fundamentals
18. AWS IAM
19. AWS networking
20. EKS
21. CloudGoat
22. Prowler
23. ScoutSuite
24. CloudFox

---

# 40. Best resource by topic

| Topic | Primary resource |
|---|---|
| Linux | **Linux Hackathon** |
| Linux → Kubernetes | **From Server to Cluster** |
| K8s fundamentals | **K8s Hackathon** |
| Kubernetes exercises | **KubernetesLabs** |
| Interactive K8s | **KubeKosh** |
| Interactive labs | **GIRUS** |
| Browser labs | **Killercoda** |
| K8s networking | **KubernetesLabs + Killercoda** |
| Helm | **KubernetesLabs** |
| ArgoCD | **KubernetesLabs** |
| RBAC | **KubeKosh + THM + K8s Hackathon** |
| Pod Security | **KubeKosh + CKS guides** |
| NetworkPolicy | **K8s Hackathon + Cilium labs** |
| Container security | **Kube-Goat + Trivy** |
| K8s pentesting | **Kubernetes Goat** |
| Runtime security | **KubeKosh + Falco + THM** |
| CIS | **kube-bench** |
| K8s posture | **Kubescape** |
| Admission | **Kyverno** |
| Runtime detection | **Falco** |
| CKS | **KubeKosh + Killercoda + CKS guides** |
| Cloud attack paths | **CloudGoat** |
| AWS assessment | **Prowler** |
| Multi-cloud assessment | **ScoutSuite** |
| AWS offensive | **Pacu / CloudFox** |

---

# 41. 12-week Kubernetes security program

## Week 1

```text
Linux
processes
permissions
networking
systemd
containers
```

**Lab:** Linux Hackathon.

## Week 2

```text
Containers
namespaces
cgroups
capabilities
Docker
container networking
```

## Week 3

```text
Kubernetes architecture
API server
etcd
scheduler
controllers
kubelet
```

**Lab:** K8s Hackathon.

## Week 4

```text
Pods
Deployments
Services
Ingress
ConfigMaps
Secrets
Volumes
```

**Lab:** KubernetesLabs.

## Week 5

```text
Networking
CNI
DNS
Service discovery
NetworkPolicy
Ingress
Gateway API
```

**Labs:** KubernetesLabs + Killercoda.

## Week 6

```text
Scheduling
taints
tolerations
affinity
anti-affinity
topology spread
```

**Lab:** KubernetesLabs.

## Week 7

```text
RBAC
ServiceAccounts
authentication
authorization
API
```

**Labs:** K8s Hackathon + KubeKosh + THM.

## Week 8

```text
Pod Security
securityContext
capabilities
seccomp
AppArmor
```

**Lab:** KubeKosh CKS track.

## Week 9

```text
kube-bench
Kubescape
Trivy
Kyverno
```

Harden your own `kind` cluster.

## Week 10

```text
Falco
runtime security
Kubernetes audit
detection
```

**Labs:** KubeKosh + Falco.

## Week 11

```text
Kubernetes Goat
Kube-Goat
```

Attack the cluster.

## Week 12

Build:

```text
secure Kubernetes platform
```

containing:

```text
kind
Helm
RBAC
NetworkPolicy
PSS
Kyverno
Trivy
Falco
Prometheus
Grafana
ArgoCD
```

Document:

```text
architecture
threat model
attack paths
security controls
detections
hardening
```

---

# 42. What you should know before CKS

You should already be able to:

```text
Create cluster
Create namespace
Create deployment
Expose service
Configure Ingress
Configure storage
Troubleshoot Pods
Troubleshoot networking
Use kubectl efficiently
Read YAML
Edit manifests quickly
Understand API resources
```

Then CKS becomes:

```text
Kubernetes
     +
security
```

rather than memorizing random security commands.

---

# 43. Recommended final sequence

```text
                         CLOUD SECURITY
                              │
                              ▼
                    Linux Hackathon
                              │
                              ▼
                  Linux hardening/security
                              │
                              ▼
                    Networking fundamentals
                              │
                              ▼
                 Cloud fundamentals / IAM
                              │
                              ▼
                         Containers
                              │
                              ▼
                    From Server to Cluster
                              │
                              ▼
                       K8s Hackathon
                              │
                    ┌─────────┴─────────┐
                    ▼                   ▼
             KubernetesLabs          KubeKosh
                    │                   │
                    └─────────┬─────────┘
                              ▼
                         Killercoda
                              │
                              ▼
                      Kubernetes Core
                              │
              ┌───────────────┼────────────────┐
              ▼               ▼                ▼
            Helm            ArgoCD          Networking
              │               │                │
              └───────────────┼────────────────┘
                              ▼
                    Kubernetes Security
                              │
              ┌───────────────┼────────────────┐
              │               │                │
             RBAC        Pod Security     NetworkPolicy
              │               │                │
              └───────────────┼────────────────┘
                              ▼
                        CKS Preparation
                              │
              ┌───────────────┼────────────────┐
              ▼               ▼                ▼
         kube-bench       Kubescape          Trivy
              │               │                │
              └───────────────┼────────────────┘
                              ▼
                       Kyverno + Falco
                              │
                              ▼
                      Kubernetes Goat
                              │
                              ▼
                       K8s attack paths
                              │
                              ▼
                       AWS / Azure / GCP
                              │
                              ▼
                    Cloud IAM + Networking
                              │
                              ▼
                       EKS / AKS / GKE
                              │
                              ▼
                    Terraform + GitOps
                              │
                              ▼
                  CloudGoat / Prowler
                              │
                              ▼
                    Cloud Detection + IR
                              │
                              ▼
                    Cloud Security Engineer
```

The strongest practical combination from the supplied roadmaps is:

> **Linux Hackathon → From Server to Cluster → K8s Hackathon → KubernetesLabs → KubeKosh → Killercoda → Kubernetes Goat → kube-bench/Kubescape/Trivy/Kyverno/Falco → EKS/AKS/GKE → CloudGoat**

---


---

# PART X — Cloud security

Everything above should be treated as the **infrastructure and cloud-native foundation**.
Only after Linux, containers, Kubernetes and Kubernetes security are comfortable should you
move into provider-specific cloud security.

The key mapping is:

```text
Linux permissions / capabilities
        ↓
Container isolation
        ↓
Kubernetes RBAC / Pod Security / NetworkPolicy
        ↓
Cloud IAM / Workload Identity / VPC
        ↓
Managed Kubernetes (EKS / AKS / GKE / Yandex Kubernetes)
```

# 3. Cloud fundamentals and cloud infrastructure

This phase is deliberately placed **before** cloud-native security. You need to understand the infrastructure that Kubernetes and workloads actually sit on.

## 3.1 Cloud concepts

Learn:

```text
IaaS
PaaS
SaaS
regions
availability zones
accounts/projects/subscriptions
resource hierarchy
control plane APIs
management plane
data plane
shared responsibility model
cloud APIs
```

## 3.2 Compute

Learn the security properties of:

```text
VMs
instances
images
instance roles
metadata services
autoscaling
managed compute
serverless functions
containers
managed Kubernetes
```

## 3.3 Storage

Learn:

```text
object storage
block storage
file storage
S3
Azure Blob
Google Cloud Storage
persistent disks
Kubernetes PV/PVC
encryption
public exposure
bucket policies
access control
```

## 3.4 Cloud networking

Learn:

```text
VPC / VNet
subnets
route tables
internet gateways
NAT
security groups
network ACLs
private endpoints
load balancers
DNS
private access
peering
VPN
```

The CbS roadmap specifically calls out native VPC integration and cloud load balancers, plus isolation mechanisms such as Private Google Access and AWS PrivateLink.

## 3.5 IAM — identity is the perimeter

Learn:

```text
users
groups
roles
policies
permissions
resource policies
identity policies
temporary credentials
federation
OIDC
MFA
least privilege
service identities
workload identities
```

The central attack-defense question is:

> **What identity is this workload using, and what can that identity do?**

---

# 4. Cloud provider learning paths

## 4.1 Yandex Cloud — Russian path

The supplied CbS roadmap contains a dedicated Yandex Cloud path.

### Base

- [ ] https://yandex.cloud/ru/training/base/?from=training-pro

### YCloud

- [ ] https://yandex.cloud/ru/training/ycloud?from=training-pro

### Compute

- [ ] https://yandex.cloud/ru/training/compute/?from=training-pro

### Kubernetes

- [ ] https://yandex.cloud/ru/training/kubernetes/?from=training-pro

### Terraform

- [ ] https://yandex.cloud/ru/training/terraform/?from=training-pro

### GitLab

- [ ] https://yandex.cloud/ru/training/gitlab/?from=training-pro

### Monitoring

- [ ] https://yandex.cloud/ru/training/monitoring/?from=training-pro

### Infrastructure protection

- [ ] https://yandex.cloud/ru/training/infrastructure-protection?from=training-pro

### DevSecOps

- [ ] https://yandex.cloud/ru/training/devsecops/?from=training-pro

### Network security

- [ ] https://yandex.cloud/ru/training/network-security?from=training-pro

### Authentication

- [ ] https://yandex.cloud/ru/training/authentication?from=training-pro

### Application defense

- [ ] https://yandex.cloud/ru/training/appdef?from=training-pro

### Cloud.ru — cybersecurity fundamentals

- [ ] https://cloud.ru/education/osnovy-kiberbezopasnosti

---

# 5. AWS / Azure / GCP fundamentals

You do not need to master every cloud simultaneously.

Recommended order:

```text
AWS fundamentals
    ↓
AWS IAM
    ↓
AWS networking
    ↓
AWS compute/storage
    ↓
EKS
    ↓
CloudGoat / Prowler / CloudFox
```

Then map the concepts to:

```text
Azure
GCP
Yandex Cloud
```

The important skill is **concept transfer**, not memorizing four different consoles.

## 5.1 Google Skills

- [ ] https://www.skills.google/catalog

Use the hands-on cloud labs.

## 5.2 Cloud security labs

- [ ] https://cloudlearn.io/labs

The supplied CbS roadmap identifies this as a free cloud-security lab source with real cloud environments and AWS/Azure security material.

## 5.3 Microsoft Learn

- [ ] https://learn.microsoft.com/training

Use the sandbox-based training environments.

## 5.4 AWS Free Tier

- [ ] https://aws.amazon.com/free

Use carefully and monitor costs.

## 5.5 AWS Well-Architected Labs — Security

- [ ] https://www.wellarchitectedlabs.com/security/

Use the security labs to learn secure AWS architecture.

---

# 6. Cloud attack fundamentals

Study cloud security offensively as well as defensively.

## 6.1 IAM privilege escalation

Learn to identify:

- over-privileged roles
- dangerous permissions
- privilege-escalation paths
- trust-policy problems
- service-to-service escalation

Practice the attack chain:

```text
Initial identity
    ↓
Enumerate permissions
    ↓
Find excessive permission
    ↓
Abuse trusted service
    ↓
Assume / obtain stronger role
    ↓
Reach objective
```

## 6.2 Storage misconfiguration

Practice identifying:

```text
public S3
public Azure Blob
public Google Cloud Storage
weak bucket policies
excessive object permissions
```

## 6.3 Metadata service / IMDS

Understand:

```text
SSRF
  ↓
metadata service
  ↓
temporary credentials
  ↓
cloud API
  ↓
privilege escalation / data access
```

Study AWS IMDSv1 and IMDSv2 and the risk of node-role credential theft.

---

# 29. Managed Kubernetes in the cloud

Move from local:

```text
kind
k3s
```

to:

```text
EKS
AKS
GKE
Yandex Cloud Kubernetes
```

Then learn:

```text
Cloud IAM
Workload Identity
VPC
cloud networking
Secrets
KMS
cloud logging
```

## Yandex Cloud Kubernetes

- [ ] https://yandex.cloud/ru/training/kubernetes/?from=training-pro

Use the Yandex Cloud Kubernetes training path from the CbS roadmap.

## Google Cloud IAM & Networking for AWS Professionals

- [ ] https://www.coursera.org/learn/gcp-fundamentals-aws

Optional supplementary material on resource hierarchy, IAM and VPCs.

## AWS Workshop Studio

- [ ] https://builder.aws.com/build/workshops

Use the LLM on Amazon EKS workshop listed in the CbS roadmap as a real-world EKS deployment exercise.

## Cisco DevNet

- [ ] https://developer.cisco.com/learning/search/?contentType=lab&page=1

Use the Cloud-Native SD-WAN with Kubernetes material for corporate-network integration.

## GCP Skills Boost

- [ ] https://www.cloudskillsboost.google/course_templates/735

Use the containerized-app / GenAI application deployment material listed in the CbS roadmap.

---

# 30. EKS security

Learn:

```text
EKS
IAM
IRSA / Pod Identity
Security Groups
VPC CNI
NetworkPolicy
Secrets
KMS
CloudTrail
GuardDuty
EKS audit logs
```

Core attack path:

```text
Pod compromise
     ↓
AWS workload identity
     ↓
temporary AWS credentials
     ↓
AWS API
     ↓
privilege escalation
```

This is the cloud-native version of Kubernetes RBAC abuse.

---

# 31. Terraform and Infrastructure as Code

Learn:

```text
provider
resource
module
variable
output
state
backend
plan
apply
```

Architecture:

```text
Terraform
   ↓
AWS API
   ↓
VPC
EC2
EKS
IAM
S3
```

Security topics:

```text
Terraform state
IAM permissions
secrets
public resources
security groups
S3
KMS
```

## IaC security tools

```text
Checkov
Trivy
KICS
Terrascan
tfsec
```

Start with:

> **Checkov + Trivy**

Pipeline:

```text
Git
 ↓
Terraform
 ↓
Checkov
 ↓
Trivy
 ↓
Review
 ↓
terraform plan
 ↓
Deployment
```

Yandex Cloud Terraform training:

- [ ] https://yandex.cloud/ru/training/terraform/?from=training-pro

---

# 32. Cloud security assessment

Learn:

```text
Prowler
ScoutSuite
CloudFox
Pacu
CloudMapper
```

## Prowler

- [ ] https://github.com/prowler-cloud/prowler

Use for:

```text
AWS security posture
CIS
compliance
IAM
networking
logging
```

## ScoutSuite

Use for:

```text
AWS
Azure
GCP
```

## CloudFox

- [ ] https://github.com/BishopFox/cloudfox

Use for:

```text
cloud attack paths
IAM
networking
privilege escalation
enumeration
```

---

# 33. Cloud offensive labs

## CloudGoat

- [ ] https://github.com/RhinoSecurityLabs/cloudgoat

Practice:

```text
IAM privilege escalation
SSRF
metadata
S3
EC2
Lambda
ECS
RDS
```

Document every scenario:

```text
Initial access
      ↓
Enumeration
      ↓
Credential discovery
      ↓
Privilege escalation
      ↓
Lateral movement
      ↓
Objective
```

Then document:

```text
Prevention
Detection
Response
```

The CbS roadmap additionally identifies scenarios involving:

```text
IAM privilege escalation
S3 misconfiguration
SSRF → metadata
```

## AWSGoat

- [ ] https://github.com/ine-labs/AWSGoat

Use as another intentionally vulnerable AWS environment.

## EKS Cluster Games

- [ ] https://eksclustergames.com

CTF-like challenges specifically around cloud security in AWS EKS.

## Haxcamp

- [ ] https://haxcamp.com/projects/

Topics:

```text
cloud security
AWS assessment
misconfiguration
```

## HackTricks Cloud

- [ ] https://cloud.hacktricks.xyz/

Free reference covering:

```text
AWS
Azure
GCP
Kubernetes
cloud exploitation
```

---

# 34. Serverless and CI/CD offensive security

## Serverless

Practice:

```text
Lambda / Functions
event-driven applications
function IAM
secrets
SSRF
cloud API access
```

Attack concept:

```text
Vulnerable function
      ↓
SSRF / code execution
      ↓
Cloud identity
      ↓
Cloud API
      ↓
Sensitive resource
```

## CI/CD pipeline poisoning

Study:

```text
GitHub Actions
GitLab CI/CD
Jenkins
build secrets
OIDC
artifact integrity
image supply chain
malicious commits
pipeline permissions
```

### CI/CD Goat

- [ ] https://github.com/cider-security-research/cicd-goat

Free self-hosted vulnerable CI/CD lab.

Practice vulnerabilities in:

```text
Jenkins
GitHub Actions
CI/CD pipelines
```

Yandex GitLab training:

- [ ] https://yandex.cloud/ru/training/gitlab/?from=training-pro

Yandex DevSecOps training:

- [ ] https://yandex.cloud/ru/training/devsecops/?from=training-pro

---

# 35. Cloud detection, monitoring and incident response

After learning attacks, learn to detect them.

## Kubernetes

Learn:

```text
Kubernetes audit logs
Falco
runtime events
API activity
RBAC changes
Pod creation
privileged workload creation
secret access
network anomalies
```

## Cloud

Learn:

```text
CloudTrail
GuardDuty
cloud audit logs
IAM events
API activity
metadata access
storage access
network flow logs
```

## Observability lab

The expanded roadmap recommends eventually adding:

```text
Prometheus
Grafana
Loki
OpenTelemetry
Tempo
```

to the local Kubernetes environment.

A useful architecture:

```text
Kubernetes
   │
   ├── metrics → Prometheus
   ├── logs    → Loki
   ├── traces  → OpenTelemetry → Tempo
   └── runtime → Falco
```

---


# Appendix A — Original expanded Kubernetes/cloud-security roadmap

The complete original **“Comprehensive Cloud Security Roadmap — Expanded Kubernetes, Free Labs, Hands-on Courses and Security Practice.md”** is preserved verbatim below so no roadmap information is lost.

---

# Comprehensive Cloud Security Roadmap

This is an expanded version of the previous roadmap, with **much more emphasis on Kubernetes** and, specifically, **free hands-on resources** similar to:

- [KubernetesLabs](https://nirgeier.github.io/KubernetesLabs/)
- [Linux Hackathon](https://linuxhackathon.com/)
- [K8s Hackathon](https://k8shackathon.com/)
- [KubeKosh](https://github.com/zeborg/kubekosh)
- [Kubernetes Goat](https://github.com/madhuakula/kubernetes-goat)

The main philosophy is:

> **Learn infrastructure → build it → break it → secure it → automate it → attack it → detect the attack.**

For cloud security, Kubernetes should be treated as a major specialization rather than a small subsection.

---

# 1. Overall roadmap

```text
Linux
  │
  ├── Linux administration
  ├── Linux networking
  ├── Linux security
  ├── Linux hardening
  └── Linux internals
          │
          ▼
Networking
  │
  ├── TCP/IP
  ├── DNS
  ├── routing
  ├── firewalls
  ├── TLS
  └── VPN
          │
          ▼
Cloud Fundamentals
  │
  ├── AWS
  ├── Azure
  ├── GCP
  ├── IAM
  ├── VPC/VNet
  ├── storage
  ├── compute
  └── cloud APIs
          │
          ▼
Containers
  │
  ├── Docker
  ├── OCI
  ├── namespaces
  ├── cgroups
  ├── capabilities
  ├── seccomp
  └── container security
          │
          ▼
Kubernetes
  │
  ├── Architecture
  ├── kubectl
  ├── workloads
  ├── networking
  ├── storage
  ├── scheduling
  ├── Helm
  └── troubleshooting
          │
          ▼
Kubernetes Security
  │
  ├── Authentication
  ├── RBAC
  ├── ServiceAccounts
  ├── Secrets
  ├── NetworkPolicy
  ├── Pod Security
  ├── Admission
  ├── seccomp
  ├── AppArmor
  ├── Falco
  ├── Kyverno
  └── audit logging
          │
          ▼
Cloud-Native Security
  │
  ├── EKS / AKS / GKE
  ├── Workload Identity
  ├── Cloud IAM
  ├── IaC
  ├── GitOps
  ├── supply chain
  └── DevSecOps
          │
          ▼
Cloud Security
  │
  ├── Cloud detection
  ├── Cloud IR
  ├── attack paths
  ├── cloud pentesting
  └── security architecture
```

---

# 2. The Kubernetes-heavy version of the roadmap

If your goal is **Cloud Security / Cloud Pentesting / DevSecOps**, I recommend spending approximately:

| Area | Approx. effort |
|---|---:|
| Linux | 10% |
| Networking | 10% |
| Cloud fundamentals | 15% |
| AWS/cloud IAM | 15% |
| Containers | 10% |
| Kubernetes fundamentals | 15% |
| Kubernetes security | **15%** |
| IaC/DevSecOps/detection | 10% |

Kubernetes deserves this much attention because modern cloud workloads frequently have this relationship:

```text
Cloud IAM
    │
    ▼
Managed Kubernetes
    │
    ▼
Kubernetes RBAC
    │
    ▼
ServiceAccount
    │
    ▼
Pod
    │
    ▼
Container
    │
    ▼
Linux kernel
```

A vulnerability or excessive permission at any layer can affect the next layer.

---

# 3. Phase 0 — Linux

Before going deep into cloud/Kubernetes security, make Linux second nature.

## Learn

### Files

```text
/etc
/var
/proc
/sys
/dev
/run
/tmp
```

### Processes

```bash
ps
top
htop
pstree
pgrep
lsof
strace
```

### Permissions

```bash
chmod
chown
chgrp
umask
sudo
```

Understand:

```text
UID
GID
SUID
SGID
sticky bit
ACLs
capabilities
```

### Services

```bash
systemctl
journalctl
systemd
```

### Networking

```bash
ip
ss
tcpdump
dig
curl
nc
iptables
nft
```

---

# 4. Linux Hackathon

## ⭐ Linux Hackathon

[Linux Hackathon](https://linuxhackathon.com/)

This is an excellent **free practical Linux foundation** for the roadmap.

It currently contains **20 hands-on challenges**, progressing from basic Linux commands through networking, containers, firewalls and troubleshooting.

The important challenges for cloud security are:

```text
05  File permissions
06  Processes
07  Users/groups
08  Bash scripting
12  Webserver
13  Server hardening
14  Containers
15  Networking
16  systemd
18  Cron
19  Firewall
20  Troubleshooting
```

Most importantly, the project itself provides a progression:

```text
Linux Hackathon
      ↓
From Server to Cluster
      ↓
K8s Hackathon
```

That makes it particularly valuable for the roadmap we're building.

---

# 5. From Server to Cluster

## ⭐⭐⭐ From Server to Cluster

[From Server to Cluster](https://fromservertocluster.com/)

This is one of the resources I would add directly to your learning sequence.

The author describes it as a **15-chapter bridge between Linux skills and Kubernetes**, with hands-on labs.

This is useful because it explains the transition:

```text
Linux
 │
 ├── processes
 ├── networking
 ├── namespaces
 ├── services
 └── containers
       │
       ▼
Kubernetes
```

Rather than treating Kubernetes as a completely separate technology.

---

# 6. Kubernetes fundamentals

Learn these before security:

```text
Cluster
Node
Control Plane
API Server
etcd
Scheduler
Controller Manager
kubelet
kube-proxy
CRI
CNI
CSI
```

Then:

```text
Pod
Deployment
ReplicaSet
DaemonSet
StatefulSet
Job
CronJob
Service
Ingress
Gateway
ConfigMap
Secret
Volume
PV
PVC
Namespace
```

---

# 7. ⭐ K8s Hackathon

## One of the best resources for your requirements

[K8s Hackathon](https://k8shackathon.com/)

This is particularly relevant to what you were asking for.

It currently contains **20 progressive hands-on challenges** covering the CKA, CKAD and CKS domains.

It includes:

```text
01 Containers
02 Pods
03 Kind cluster
04 Deployments
05 Services
06 Ingress / Gateway API
07 Storage
08 ConfigMaps / Secrets
09 RBAC / Security
10 Autoscaling
11 Helm / Kustomize
12 Observability
13 Troubleshooting
...
```

And importantly:

> **Challenge 03 explicitly builds a local multi-node Kubernetes cluster using Kind.**

This makes it an especially good fit for your preferred learning model.

### Coverage

```text
CKA
├── cluster
├── nodes
├── networking
├── storage
├── scheduling
├── troubleshooting
└── administration

CKAD
├── applications
├── workloads
├── configuration
├── services
├── storage
└── observability

CKS
├── RBAC
├── Pod Security
├── NetworkPolicy
├── security contexts
├── runtime security
└── security hardening
```

---

# 8. ⭐ KubernetesLabs

## Nir Geier — KubernetesLabs

[KubernetesLabs](https://nirgeier.github.io/KubernetesLabs/Tasks/) 

This is another **high-priority resource**.

Unlike many Kubernetes courses, it is structured around **individual practical tasks**, each with instructions and solutions.

The current task catalog includes:

### Core Kubernetes

```text
Kubernetes CLI
Pod debugging
Deployments
Services
ConfigMaps
Secrets
Networking
Service discovery
Scheduling
Affinity
Anti-affinity
Taints
Tolerations
Topology spread
```

### Kubernetes ecosystem

```text
Helm
ArgoCD
Kubebuilder
KEDA
Harbor
Air-gapped Kubernetes
```

The Helm section includes:

```text
chart creation
packaging
templating
repositories
deployment
best practices
```

The ArgoCD section includes:

```text
CLI
application deployment
GitOps
App of Apps
sync waves
fleet management
```

The Harbor + ArgoCD section is particularly useful for **supply-chain / DevSecOps security**.

### My rating

| Area | Rating |
|---|---:|
| Kubernetes fundamentals | ⭐⭐⭐⭐⭐ |
| kubectl | ⭐⭐⭐⭐⭐ |
| Networking | ⭐⭐⭐⭐ |
| Scheduling | ⭐⭐⭐⭐⭐ |
| Helm | ⭐⭐⭐⭐⭐ |
| ArgoCD | ⭐⭐⭐⭐⭐ |
| Security | ⭐⭐⭐ |
| CKA | ⭐⭐⭐⭐ |
| CKAD | ⭐⭐⭐⭐ |
| CKS | ⭐⭐⭐ |

Use this **alongside**, rather than instead of, security-specific labs.

---

# 9. ⭐ KubeKosh

## Interactive Kubernetes Playground

[KubeKosh](https://github.com/zeborg/kubekosh)

This is one of the most interesting new resources.

It runs a real **K3s cluster inside a Docker container** and provides a browser terminal with automated scenario validation.

You don't need:

```text
AWS
Azure
GCP
```

or even a Kubernetes installation.

You can start it locally with Docker.

### Coverage

The current scenarios include:

```text
Kubernetes Basics        40 scenarios
Gateway API              10
CKAD                     25
CKA                      40
CKS                      25
Istio                    10
Traefik                  10
HAProxy                  10
Falco                    10
```

The **CKS track** specifically covers:

```text
Pod Security Admission
NetworkPolicy
seccomp
AppArmor
RBAC
```

and the **Falco track** covers runtime threat detection.

This is probably one of the **best additions to your Kubernetes-security learning stack**.

---

# 10. ⭐ GIRUS

[GIRUS](https://girus.io/)

GIRUS is a free/open-source interactive lab platform from LINUXtips.

It provides isolated practical environments for:

```text
Kubernetes
Docker
AWS
Terraform
DevOps
```

and runs locally through Docker/Kubernetes.

The important feature is:

```text
guided task
     ↓
interactive terminal
     ↓
real environment
     ↓
validation
```

This is much closer to the learning style of KubernetesLabs than a conventional video course.

---

# 11. ⭐ KubeLab

[KubeLab](https://github.com/natrontech/kubelab)

KubeLab is another web-based interactive Kubernetes training platform with practical exercises designed around Kubernetes workshops.

I would put it below:

```text
K8s Hackathon
KubernetesLabs
KubeKosh
GIRUS
```

but it is worth checking as an additional exercise source.

---

# 12. ⭐ Kubernetes practical exercises

[Kubernetes Practical Exercises — Hands-on](https://github.com/seifrajhi/Kubernetes-practical-exercises-Hands-on)

This is useful if you want a **large repository of exercises rather than a polished course**.

It explicitly recommends using:

```text
kind
k3d
k3s
Docker Desktop
```

for local practice.

It also contains Kubernetes networking guides where topics are accompanied by dedicated hands-on labs.

---

# 13. Kubernetes security

Once you can comfortably operate a cluster, start this phase.

```text
Kubernetes
    │
    ├── Authentication
    ├── Authorization
    │      └── RBAC
    │
    ├── Admission
    │      ├── PSS
    │      └── Kyverno
    │
    ├── Network
    │      └── NetworkPolicy
    │
    ├── Workload
    │      └── SecurityContext
    │
    ├── Runtime
    │      └── Falco
    │
    └── Audit
           └── Kubernetes audit logs
```

---

# 14. Kubernetes authentication

Learn:

```text
Client certificates
ServiceAccount tokens
OIDC
Cloud IAM
```

For cloud Kubernetes:

```text
AWS IAM
    ↓
EKS
    ↓
Kubernetes identity
    ↓
RBAC
```

Similarly:

```text
Azure Entra ID → AKS
GCP IAM → GKE
```

---

# 15. Kubernetes RBAC

This should be one of your strongest skills.

Learn:

```text
Role
ClusterRole
RoleBinding
ClusterRoleBinding
ServiceAccount
User
Group
Subject
Verb
Resource
API Group
```

Practice:

```bash
kubectl auth can-i
```

Build:

```text
viewer
developer
namespace-admin
cluster-admin
```

Then investigate:

```text
Can viewer read Secrets?

Can developer create Pods?

Can developer create Roles?

Can developer create RoleBindings?

Can ServiceAccount access another namespace?

Can it create a privileged Pod?
```

---

# 16. RBAC attack path

Practice this model:

```text
Compromised application
        ↓
Pod RCE
        ↓
ServiceAccount
        ↓
Token
        ↓
Kubernetes API
        ↓
RBAC enumeration
        ↓
Secrets
        ↓
Pod creation
        ↓
Privilege escalation
```

Then fix it.

This is much more useful than simply memorizing RBAC YAML.

---

# 17. TryHackMe Kubernetes resources

TryHackMe has an excellent Kubernetes security curriculum conceptually, although **the current access status matters**.

For example, the current **Intro to Kubernetes** room is marked Premium, despite TryHackMe advertising that the platform has hundreds of free rooms.

Therefore I would **not count TryHackMe as your primary free Kubernetes curriculum**.

Instead, use its rooms as supplementary material whenever they are accessible to your account.

---

# 18. TryHackMe — Cluster Hardening

[Cluster Hardening](https://tryhackme.com/room/clusterhardening)

Excellent security-focused material.

It covers:

```text
cluster hardening
secure configuration
Kubernetes architecture
security considerations
```

and includes a practical VM exercise.

### Use it after

```text
K8s Hackathon
        +
KubernetesLabs
```

---

# 19. TryHackMe — K8s Best Security Practices

[K8s Best Security Practices](https://tryhackme.com/room/k8sbestsecuritypractices)

This is particularly relevant for your interests.

It covers:

```text
ServiceAccounts
RBAC
Roles
RoleBindings
Kubernetes API
security best practices
```

The learning objectives explicitly include creating Roles and RoleBindings and understanding Kubernetes API requests.

---

# 20. TryHackMe — K8s Runtime Security

[K8s Runtime Security](https://tryhackme.com/room/k8sruntimesecurity)

Focuses on security **after workloads are running**.

Topics include:

```text
runtime attacks
privilege escalation
runtime security
Falco
Kubernetes runtime monitoring
```



This is exactly the layer many Kubernetes beginners skip.

---

# 21. TryHackMe — Kubernetes Hardening module

[Kubernetes Hardening](https://tryhackme.com/module/kubernetes-hardening)

The module currently combines:

```text
Cluster Hardening
K8s Best Security Practices
Microservices Architectures
K8s Runtime Security
Secure GitOps
```



The downside is that access to individual rooms may be Premium, so treat this as **supplementary**, not your definition of a free course.

---

# 22. Kubernetes Goat

## ⭐⭐⭐⭐⭐

[Kubernetes Goat](https://github.com/madhuakula/kubernetes-goat)

This should absolutely be in your cloud-security roadmap.

It is an intentionally vulnerable Kubernetes cluster designed specifically for learning Kubernetes security through hands-on exploitation.

Think of it as:

```text
Kubernetes security
        +
CTF
        +
attack simulation
```

You should use it after learning:

```text
Kubernetes
RBAC
containers
networking
Linux
```

---

# 23. Kube-Goat

[ksoclabs/kube-goat](https://github.com/ksoclabs/kube-goat)

Another deliberately vulnerable Kubernetes cluster.

I would use:

```text
Kubernetes Goat
        ↓
Kube-Goat
```

as two separate offensive practice environments.

---

# 24. Kubernetes attack-chain lab

Once you've completed Kubernetes Goat, build your own.

Example:

```text
Web application
      ↓
RCE
      ↓
Container
      ↓
ServiceAccount
      ↓
Kubernetes API
      ↓
RBAC
      ↓
Secret
      ↓
Pod creation
      ↓
Privileged workload
      ↓
Node
```

Then create the defensive version:

```text
NetworkPolicy
RBAC
PSS
seccomp
AppArmor
Kyverno
Falco
audit logs
```

---

# 25. K8s security tooling

Build a lab containing:

```text
                 K8S SECURITY LAB

                    Kubernetes
                         │
          ┌──────────────┼──────────────┐
          │              │              │
        RBAC       NetworkPolicy    Pod Security
          │              │              │
          ▼              ▼              ▼
      kubectl         Cilium/Calico     PSS
                         │
                         │
              ┌──────────┴──────────┐
              │                     │
           Kyverno                Trivy
              │                     │
              ▼                     ▼
        Admission              Scanning
                                   
                         │
                         ▼
                       Falco
                         │
                         ▼
                   Runtime Security
```

---

# 26. kube-bench

[kube-bench](https://github.com/aquasecurity/kube-bench)

Run it against your cluster.

It checks Kubernetes configuration against CIS Kubernetes Benchmark recommendations.

Workflow:

```text
Run kube-bench
      ↓
Findings
      ↓
Understand each finding
      ↓
Fix it
      ↓
Run again
```

Don't simply run it and paste the report into a README.

Understand every finding.

---

# 27. Kubescape

[Kubescape](https://github.com/kubescape/kubescape)

Use it for:

```text
Kubernetes posture
CIS
NSA/CISA
misconfigurations
risk
compliance
```

Compare:

```text
kube-bench
     vs
Kubescape
```

and understand what each is measuring.

---

# 28. Trivy

[Trivy](https://github.com/aquasecurity/trivy)

Use it everywhere:

```text
Docker image
Filesystem
Git repository
Kubernetes
Helm
Terraform
IaC
Secrets
SBOM
Vulnerabilities
```

Your workflow should become:

```text
Build
 ↓
Trivy
 ↓
Fix
 ↓
Trivy
 ↓
Deploy
 ↓
Kubernetes
```

---

# 29. Kyverno

[Kyverno](https://github.com/kyverno/kyverno)

Learn to enforce:

```text
No privileged containers
No root containers
No :latest
Approved registries only
Required labels
Required resource limits
Required NetworkPolicy
Signed images
```

For example:

```text
Developer
   │
   ▼
kubectl apply
   │
   ▼
Kyverno
   │
   ├── compliant → allow
   │
   └── violation → deny
```

---

# 30. Falco

Use:

[Falco](https://github.com/falcosecurity/falco)

Practice detecting:

```text
shell spawned in container
unexpected process
sensitive file access
privilege escalation
unexpected network connection
container runtime abuse
```

The important distinction:

```text
Trivy
  =
before runtime

Kyverno
  =
at admission

Falco
  =
during runtime
```

---

# 31. Kubernetes security certification resources

## CKS Study Guide

[Isovalent CKS Study Guide](https://github.com/isovalent/CKS-Study-Guide)

This is an excellent security-focused reference.

It includes resources for:

```text
NetworkPolicy
Cilium
Pod-to-pod encryption
mTLS
microservice security
Cilium security
```

and links to hands-on labs.

---

## CKS Preparation Guide

[leandrocostam/cks-preparation-guide](https://github.com/leandrocostam/cks-preparation-guide)

This is organized around the current CKS curriculum and links heavily to official Kubernetes documentation.

Use it as a **study map**, not as your only hands-on resource.

---

# 32. CKS practice repository

[snigdhasambitak/cks](https://github.com/snigdhasambitak/cks)

Contains CKS practice material including:

```text
Contexts
Falco
API server security
```

and points learners toward Killercoda CKA/CKS scenarios.

---

# 33. ViktorUJ Kubernetes/AWS labs

[ViktorUJ/cks](https://github.com/ViktorUJ/cks)

This is particularly interesting because it combines:

```text
CKA
CKS
CKAD
EKS
AWS
KCSA
KCNA
```

with automated lab creation and mock exams.

It does require AWS infrastructure for several labs, so this is not the same as a completely local `kind` course.

Use it later for:

```text
Kubernetes
       ↓
AWS
       ↓
EKS
       ↓
Cloud-native security
```

---

# 34. Killercoda

## ⭐⭐⭐⭐⭐

[Killercoda](https://killercoda.com/)

This is one of the most important interactive platforms to know.

It provides browser-based disposable Linux/Kubernetes environments with no local setup required.

The free tier currently provides access to free scenarios, although paid memberships unlock additional functionality and courses.

Use it for:

```text
Kubernetes
Docker
Linux
Networking
DevOps
CKA-style scenarios
CKS-style scenarios
```

---

# 35. Killercoda learning strategy

Search its scenarios for:

```text
Kubernetes
CKA
CKS
RBAC
NetworkPolicy
security
Cilium
Falco
Helm
Ingress
troubleshooting
```

A particularly useful progression is:

```text
Killer Shell CKA
       ↓
Kubernetes scenarios
       ↓
Killer Shell CKS
       ↓
security scenarios
```

The CKS community resources specifically recommend studying Killercoda's CKA and CKS scenarios.

---

# 36. K8s security learning stack

I would organize your Kubernetes resources like this:

```text
                 KUBERNETES FUNDAMENTALS

                         │
          ┌──────────────┼──────────────┐
          │              │              │
   K8s Hackathon   KubernetesLabs    KubeKosh
          │              │              │
          └──────────────┼──────────────┘
                         │
                         ▼
                    Killercoda
                         │
                         ▼
                 Kubernetes security
                         │
          ┌──────────────┼──────────────┐
          │              │              │
     CKS Guides       THM rooms      Kube Goat
          │              │              │
          └──────────────┼──────────────┘
                         │
                         ▼
                   Security tools
                         │
        ┌────────────────┼────────────────┐
        │                │                │
    kube-bench       Kubescape        Trivy
        │                │                │
        └────────────────┼────────────────┘
                         │
                 ┌───────┴───────┐
                 │               │
              Kyverno          Falco
                 │               │
                 └───────┬───────┘
                         ▼
                  Cloud Kubernetes
                         │
                    EKS / AKS / GKE
```

---

# 37. Helm

Helm should be considered part of Kubernetes security.

Learn:

```text
Chart
values.yaml
templates
release
repository
dependencies
hooks
OCI registry
```

Security issues:

```text
template injection
malicious charts
untrusted repositories
secrets in values
supply-chain attacks
```

Best practice:

```text
Helm
 ↓
Trivy
 ↓
Kyverno
 ↓
signed image
 ↓
deployment
```

Use the **Helm tasks in KubernetesLabs** extensively.

---

# 38. ArgoCD / GitOps security

Learn:

```text
Git
 ↓
ArgoCD
 ↓
Kubernetes
```

Then security:

```text
Git compromise
 ↓
malicious manifest
 ↓
ArgoCD
 ↓
cluster
```

Study:

- ArgoCD RBAC
- repository credentials
- secrets
- application permissions
- project restrictions
- sync policies
- image signing
- admission policies

KubernetesLabs has a dedicated ArgoCD practical track including App of Apps, sync waves and fleet management.

---

# 39. Harbor / registry security

Learn:

```text
Developer
    ↓
CI
    ↓
Image
    ↓
Harbor
    ↓
Kubernetes
```

Security:

```text
image scanning
RBAC
signing
provenance
vulnerability scanning
registry access
```

The KubernetesLabs **Harbor + ArgoCD Airgap** tasks are particularly useful here because they combine registry, ingress, GitOps, image mirroring and offline deployment.

---

# 40. Containers before CKS

Do not jump directly from Kubernetes basics into CKS.

Study:

```text
Linux namespaces
cgroups
capabilities
seccomp
AppArmor
SELinux
runc
containerd
OCI
```

Understand:

```text
Pod
 ↓
container
 ↓
container runtime
 ↓
Linux namespaces/cgroups
 ↓
Linux kernel
```

This is essential for understanding container escape.

---

# 41. Container security labs

Practice:

### Lab 1

Run:

```text
root container
```

Then:

```text
non-root container
```

Compare privileges.

### Lab 2

Inspect:

```text
capabilities
namespaces
cgroups
```

### Lab 3

Experiment with:

```text
privileged
hostPID
hostNetwork
hostPath
CAP_SYS_ADMIN
```

### Lab 4

Apply:

```text
seccomp
AppArmor
readOnlyRootFilesystem
drop capabilities
runAsNonRoot
```

---

# 42. Cloud + Kubernetes security

Now connect Kubernetes to cloud.

For AWS:

```text
AWS Account
     │
     ▼
VPC
     │
     ▼
EKS
     │
     ├── Control plane
     │
     └── Worker nodes
              │
              ▼
            Pods
```

Security boundaries:

```text
AWS IAM
   ↓
EKS identity
   ↓
Kubernetes RBAC
   ↓
ServiceAccount
   ↓
Pod
```

---

# 43. EKS security

Learn:

```text
EKS
IAM
IRSA / Pod Identity
Security Groups
VPC CNI
NetworkPolicy
Secrets
KMS
CloudTrail
GuardDuty
EKS audit logs
```

The important attack path is:

```text
Pod compromise
    ↓
AWS workload identity
    ↓
temporary AWS credentials
    ↓
AWS API
    ↓
privilege escalation
```

---

# 44. Terraform

Learn:

```text
provider
resource
module
variable
output
state
backend
plan
apply
```

Then:

```text
Terraform
   ↓
AWS API
   ↓
VPC
EC2
EKS
IAM
S3
```

Security:

```text
Terraform state
IAM permissions
secrets
public resources
security groups
S3
KMS
```

---

# 45. IaC security

Tools:

```text
Checkov
Trivy
KICS
Terrascan
tfsec
```

Start with:

> **Checkov + Trivy**

Pipeline:

```text
Git
 ↓
Terraform
 ↓
Checkov
 ↓
Trivy
 ↓
Review
 ↓
terraform plan
 ↓
Deployment
```

---

# 46. Cloud security attack labs

## CloudGoat

[CloudGoat](https://github.com/RhinoSecurityLabs/cloudgoat)

Use this after learning AWS.

Practice:

```text
IAM privilege escalation
SSRF
metadata
S3
EC2
Lambda
ECS
RDS
```

The key is to document every scenario as:

```text
Initial access
       ↓
Enumeration
       ↓
Credential discovery
       ↓
Privilege escalation
       ↓
Lateral movement
       ↓
Objective
```

Then write:

```text
Prevention
Detection
Response
```

---

# 47. Cloud security assessment

Learn:

```text
Prowler
ScoutSuite
CloudFox
Pacu
CloudMapper
```

Use:

### Prowler

For:

```text
AWS security posture
CIS
compliance
IAM
networking
logging
```

### ScoutSuite

For:

```text
AWS
Azure
GCP
```

### CloudFox

For:

```text
cloud attack paths
IAM
networking
privilege escalation
```

---

# 48. Free interactive resource ranking

If your primary requirement is:

> **"I want something like KubernetesLabs where I actually perform tasks rather than watch videos."**

I would rank the resources like this:

| Rank | Resource | Hands-on | Free | Local | Security |
|---:|---|:---:|:---:|:---:|:---:|
| 🥇 | **K8s Hackathon** | ⭐⭐⭐⭐⭐ | ✅ | Kind | ⭐⭐⭐⭐ |
| 🥈 | **KubernetesLabs** | ⭐⭐⭐⭐⭐ | ✅ | ✅ | ⭐⭐⭐ |
| 🥉 | **KubeKosh** | ⭐⭐⭐⭐⭐ | ✅ | Docker | ⭐⭐⭐⭐⭐ |
| 4 | **GIRUS** | ⭐⭐⭐⭐⭐ | ✅ | Docker | ⭐⭐⭐ |
| 5 | **Killercoda** | ⭐⭐⭐⭐⭐ | Many free scenarios | Browser | ⭐⭐⭐⭐ |
| 6 | **Kubernetes Goat** | ⭐⭐⭐⭐⭐ | ✅ | K8s | ⭐⭐⭐⭐⭐ |
| 7 | **Kube-Goat** | ⭐⭐⭐⭐ | ✅ | K8s | ⭐⭐⭐⭐⭐ |
| 8 | **KubeLab** | ⭐⭐⭐⭐ | Open source | Browser/local | ⭐⭐⭐ |
| 9 | **Practical Exercises** | ⭐⭐⭐⭐ | ✅ | Kind/k3d | ⭐⭐⭐ |
| 10 | **TryHackMe K8s** | ⭐⭐⭐⭐ | Some free content | Browser/VM | ⭐⭐⭐⭐⭐ |

---

# 49. The best completely free Kubernetes stack

If I wanted to minimize paid resources, I would use:

```text
                 KUBERNETES

                    Linux
                      │
                      ▼
             Linux Hackathon
                      │
                      ▼
            From Server to Cluster
                      │
                      ▼
                K8s Hackathon
                      │
            ┌─────────┴─────────┐
            │                   │
            ▼                   ▼
     KubernetesLabs          KubeKosh
            │                   │
            └─────────┬─────────┘
                      ▼
                 Killercoda
                      │
                      ▼
              Kubernetes security
                      │
        ┌─────────────┼─────────────┐
        ▼             ▼             ▼
   Kubernetes      CKS Guides    Kubernetes
      Goat                        security labs
        │
        ▼
     kube-bench
     Kubescape
     Trivy
     Kyverno
     Falco
```

This is much more practical than buying several video courses.

---

# 50. Recommended Kubernetes sequence

## Stage 1 — Linux

Use:

- Linux Hackathon

Focus:

```text
permissions
processes
networking
systemd
containers
firewall
```

---

## Stage 2 — Linux → Kubernetes

Use:

- From Server to Cluster

Focus:

```text
Linux
 ↓
containers
 ↓
orchestration
 ↓
Kubernetes
```

---

## Stage 3 — Kubernetes fundamentals

Use:

- K8s Hackathon
- KubernetesLabs
- KubeKosh
- Killercoda

Learn:

```text
Pods
Deployments
Services
Networking
Storage
Scheduling
Config
Secrets
Troubleshooting
```

---

## Stage 4 — Kubernetes ecosystem

Use:

- KubernetesLabs

Learn:

```text
Helm
ArgoCD
KEDA
Kubebuilder
Harbor
```

---

## Stage 5 — Kubernetes security

Use:

- KubeKosh CKS track
- Killercoda
- TryHackMe Cluster Hardening
- TryHackMe K8s Best Security Practices
- CKS Study Guides

Learn:

```text
RBAC
ServiceAccounts
Pod Security
NetworkPolicy
seccomp
AppArmor
API security
```

---

## Stage 6 — Offensive Kubernetes security

Use:

- Kubernetes Goat
- Kube-Goat

Practice:

```text
container compromise
RBAC abuse
secrets
service accounts
API attacks
privilege escalation
container escape
```

---

## Stage 7 — Runtime security

Use:

- KubeKosh Falco scenarios
- TryHackMe K8s Runtime Security
- Falco

Learn:

```text
syscalls
eBPF
runtime events
Falco rules
detection
response
```

---

## Stage 8 — Cloud Kubernetes

Move to:

```text
EKS
AKS
GKE
```

Then learn:

```text
Cloud IAM
Workload Identity
VPC
Cloud networking
Secrets
KMS
Cloud logging
```

---

# 51. 12-week Kubernetes security program

If you want a concentrated program:

## Week 1

```text
Linux
processes
permissions
networking
systemd
containers
```

Linux Hackathon.

---

## Week 2

```text
Containers
namespaces
cgroups
capabilities
Docker
container networking
```

---

## Week 3

```text
Kubernetes architecture
API server
etcd
scheduler
controllers
kubelet
```

K8s Hackathon.

---

## Week 4

```text
Pods
Deployments
Services
Ingress
ConfigMaps
Secrets
Volumes
```

KubernetesLabs.

---

## Week 5

```text
Networking
CNI
DNS
Service discovery
NetworkPolicy
Ingress
Gateway API
```

KubernetesLabs + Killercoda.

---

## Week 6

```text
Scheduling
taints
tolerations
affinity
anti-affinity
topology spread
```

KubernetesLabs.

---

## Week 7

```text
RBAC
ServiceAccounts
authentication
authorization
API
```

K8s Hackathon + KubeKosh + THM.

---

## Week 8

```text
Pod Security
securityContext
capabilities
seccomp
AppArmor
```

KubeKosh CKS track.

---

## Week 9

```text
kube-bench
Kubescape
Trivy
Kyverno
```

Harden your own `kind` cluster.

---

## Week 10

```text
Falco
runtime security
Kubernetes audit
detection
```

KubeKosh + Falco.

---

## Week 11

```text
Kubernetes Goat
Kube-Goat
```

Attack the cluster.

---

## Week 12

Build:

```text
secure Kubernetes platform
```

containing:

```text
kind
Helm
RBAC
NetworkPolicy
PSS
Kyverno
Trivy
Falco
Prometheus
Grafana
ArgoCD
```

Document:

```text
architecture
threat model
attack paths
security controls
detections
hardening
```

---

# 52. The ultimate local lab

Your workstation should eventually contain:

```text
                         Linux
                           │
                         Docker
                           │
                   ┌───────┴───────┐
                   │               │
                  Kind            K3s
                   │
             Kubernetes
                   │
       ┌───────────┼────────────┐
       │           │            │
     Helm        ArgoCD       Cilium
       │           │            │
       └───────────┼────────────┘
                   │
              Security
                   │
      ┌────────────┼─────────────┐
      │            │             │
   Kyverno       Trivy         Falco
      │            │             │
      └────────────┼─────────────┘
                   │
              Assessment
                   │
          ┌────────┴─────────┐
          │                  │
      kube-bench          Kubescape
```

Then add:

```text
Prometheus
Grafana
Loki
OpenTelemetry
Tempo
```

for observability.

---

# 53. What you should know before CKS

Don't start CKS immediately.

You should already be able to do:

```text
Create cluster
Create namespace
Create deployment
Expose service
Configure Ingress
Configure storage
Troubleshoot Pods
Troubleshoot networking
Use kubectl efficiently
Read YAML
Edit manifests quickly
Understand API resources
```

Then CKS becomes:

```text
Kubernetes
     +
security
```

rather than:

```text
memorize random security commands
```

---

# 54. Cloud security project progression

## Project 1

### Secure Linux server

```text
Ubuntu
SSH
users
sudo
auditd
firewall
Fail2Ban
AppArmor
logging
```

---

## Project 2

### Secure Docker host

```text
Docker
Docker Bench
Trivy
rootless containers
capabilities
seccomp
AppArmor
```

---

## Project 3

### Secure Kubernetes cluster

```text
kind
RBAC
PSS
NetworkPolicy
Kyverno
Trivy
kube-bench
Kubescape
Falco
```

---

## Project 4

### Vulnerable Kubernetes cluster

Use:

```text
Kubernetes Goat
Kube-Goat
```

Attack:

```text
Pod
 ↓
ServiceAccount
 ↓
RBAC
 ↓
Secrets
 ↓
Node
```

---

## Project 5

### Secure GitOps platform

```text
GitHub
   ↓
CI
   ↓
Trivy
   ↓
SBOM
   ↓
Image signing
   ↓
Harbor
   ↓
ArgoCD
   ↓
Kyverno
   ↓
Kubernetes
```

---

## Project 6

### Cloud-native attack chain

```text
AWS
 │
 └── EKS
       │
       └── Pod
             │
             └── ServiceAccount
                    │
                    └── AWS IAM
                           │
                           └── S3
```

Document:

```text
attack
impact
detection
prevention
remediation
```

---

# 55. Resource hierarchy I recommend for you

Given your existing Kubernetes/DevOps work, I would **not** spend months on generic Kubernetes video courses.

Use this instead:

### Tier 1 — Main courses

1. **K8s Hackathon**
2. **KubernetesLabs**
3. **KubeKosh**
4. **GIRUS**
5. **Killercoda**

### Tier 2 — Security

6. **Kubernetes Goat**
7. **Kube-Goat**
8. **KubeKosh CKS/Falco**
9. **TryHackMe Kubernetes security rooms**
10. **CKS Study Guides**

### Tier 3 — Tool practice

11. **kube-bench**
12. **Kubescape**
13. **Trivy**
14. **Kyverno**
15. **Falco**
16. **Cilium**

### Tier 4 — Cloud

17. AWS fundamentals
18. AWS IAM
19. AWS networking
20. EKS
21. CloudGoat
22. Prowler
23. ScoutSuite
24. CloudFox

---

# 56. Best resources by topic

| Topic | Best free resource |
|---|---|
| Linux | **Linux Hackathon** |
| Linux → K8s | **From Server to Cluster** |
| K8s fundamentals | **K8s Hackathon** |
| Kubernetes exercises | **KubernetesLabs** |
| Interactive K8s | **KubeKosh** |
| Interactive labs | **GIRUS** |
| Browser labs | **Killercoda** |
| K8s networking | **KubernetesLabs + Killercoda** |
| Helm | **KubernetesLabs** |
| ArgoCD | **KubernetesLabs** |
| RBAC | **KubeKosh + THM + K8s Hackathon** |
| Pod Security | **KubeKosh + CKS guides** |
| NetworkPolicy | **K8s Hackathon + Cilium labs** |
| Container security | **Kube Goat + Trivy** |
| K8s pentesting | **Kubernetes Goat** |
| K8s vulnerable labs | **Kubernetes Goat / Kube-Goat** |
| Runtime security | **KubeKosh + Falco + THM** |
| CIS | **kube-bench** |
| K8s posture | **Kubescape** |
| Admission | **Kyverno** |
| Runtime detection | **Falco** |
| CKS | **KubeKosh + Killercoda + CKS guides** |
| Cloud attack paths | **CloudGoat** |
| AWS assessment | **Prowler** |
| Multi-cloud assessment | **ScoutSuite** |
| AWS offensive | **Pacu / CloudFox** |

---



