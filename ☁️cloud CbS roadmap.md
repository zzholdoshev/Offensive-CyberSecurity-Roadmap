#kubernetes #cloud #yandex

# 🧪 Kubernetes / Containers / Network

^e07136
## A Comprehensive Hardening and Risk Mitigation Strategy for Cloud and Container Infrastructures: A Practical Guide and Roadmap (2025-2026)

> Modern information systems architecture has shifted to distributed microservice environments managed via Kubernetes in the cloud. This has expanded the attack surface, requiring hardening systems at all levels—from the Linux kernel to cloud IAM. This report presents protection mechanisms and a structured roadmap for learning.

## Chapter 1: Fundamental Hardening of the Linux Operating System

Cloud security starts with the Linux OS. Hardening is the process of reducing the attack surface through software minimization and strict permissions.

### 1.1. Rwx Permissions and ACLs

The rwx (read, write, execute) bit system is the foundation of security. Errors in directory permissions often lead to data compromise. For security, the principle of least privilege and the use of the Sticky Bit (for example, in /tmp) are recommended, ensuring that only the owner can delete files. ACLs allow granular access control for specific users.

### 1.2. sudo Security

Incorrect configuration in /etc/sudoers is a critical risk. Vulnerabilities like CVE-2019-14287 demonstrate that errors in UID handling can bypass restrictions. Modern hardening includes disabling ALL=(ALL:ALL) ALL, using requirety, and mandatory call auditing.

## Chapter 2: Container Isolation and Kernel Primitives

Containers use the host kernel, so isolation mechanisms are critical to preventing container escapes.

- **Namespaces:** Virtualize resources (PID, NET, MNT, USER), creating the illusion of an isolated system.

- **Cgroups:** Limit resource consumption (CPU, memory, PIDs), preventing DoS attacks such as "fork bombs."

- **Seccomp and Capabilities:** Seccomp filters kernel system calls, while Capabilities fragment root privileges, allowing only the necessary ones (e.g., CAP_NET_BIND_SERVICE).

## Chapter 3: Advanced Sandboxes: gVisor and MicroVM

Standard containers are not sufficient for running untrusted code (e.g., AI agents).

- **gVisor:** Intercepts user-space system calls, allowing only about 20 safe calls to the host kernel.

- **MicroVM (Kata, Firecracker):** Runs each container in a separate, lightweight virtual machine with its own kernel, providing hardware isolation.

## Chapter 4: Kubernetes Security and Operations

Kubernetes requires protection for the Control Plane, etcd, and workloads.

- **Network Policies:** By default, all pods in K8s can see each other. The Zero Trust model requires the implementation of `Network Policies` to limit traffic.

- **RBAC and Admission Control:** Errors in service account permissions are a common cause of hacks. Tools like `Kyverno` or `OPA` block the creation of insecure resources.

## Chapter 5: Kubernetes in Cloud Environments (EKS, GKE, AKS)

Working in the cloud shifts the focus to integrating K8s with the provider's infrastructure.

- **Cloud IAM:** In the cloud, identity is the new perimeter. Using `Workload Identity` allows pods to access cloud resources (S3, BigQuery) without static keys.

- **Network Integration:** Cloud K8s uses native VPCs and load balancers. It is important to configure `Private Google Access` or `AWS PrivateLink` to isolate traffic within the cloud.

- **Specific Threats:** Attacks through the metadata service (IMDSv2) in AWS can lead to theft of node roles.

## Chapter 6: Roadmap

### Level 1: Linux Fundamentals and Access Rights. Covered in [[🏴Pentest roadmap#^5207fe|pentest roadmap]]

- [ ] **Linux Fundamentals (TryHackMe)**: Practicing `chmod`, `chown`, and system structure. [Lab](https://tryhackme.com/module/linux-fundamentals) ✅ 2026-04-03

- [ ] **Agent Sudo (TryHackMe)**: Hacking and securing sudo settings. [Lab](https://tryhackme.com/room/agentsudoctf)

- [ ] **Scenario "La Rinconada" (SadServers)**: A live challenge to exploit sudo to gain root. [Lab](https://sadservers.com/scenarios)

- [ ] SadServers: "Taipei" — Hacking and Firewall Configuration (Port Knocking). Link: sadservers.com/scenario/taipei

### Level 2: Containers and Sandboxes

* First steps:
* [ ] https://k8sgames.com - #kubernetes in-browser game (also look up materials in [[#^8d161b|links]])
* [ ] https://youtu.be/TlHvYWVUZyc?si=rqzJ7KCWdv6YYiPZ - brief explanation of k8s
* [ ] https://training.play-with-kubernetes.com/ - play with k8s
- [ ] **Container Hardening (TryHackMe)**: Step-by-step Docker hardening setup. [Laba](https://tryhackme.com/room/containerhardening) PAID - find an equivalent

- [ ] **Namespaces & Cgroups (Medium/GitHub)**: Manual container creation via `unshare`. [Laba](https://github.com/TamimEhsan/Simple-Sandbox)

- [ ] **Sandbox gVisor (Killercoda)**: Launching Isolated Pods in K8s with gVisor. [Lab](https://killercoda.com/killer-shell-cks/scenario/sandbox-gvisor)

### Level 3: Kubernetes in the Cloud (Yandex/EKS/GKE) — Administration and Basics
#### For Yandex K8s, this is covered [[☁️cloud CbS roadmap#^9737c2|here]]
#### optional
- [ ] **Google Cloud IAM & Networking for AWS Professionals (Coursera)**: Exploring resource hierarchy and VPCs in the context of K8s. [Lab](https://www.coursera.org/learn/gcp-fundamentals-aws)

- [ ] **Large Language Model (LLM) on Amazon EKS (AWS Workshop Studio)**: Deploying real-world workloads to EKS. [Lab](https://builder.aws.com/build/workshops)

- [ ] **Cloud-Native SD-WAN with K8s (Cisco DevNet)**: Integrating a cluster with a corporate network. [Lab](https://developer.cisco.com/learning/search/?contentType=lab&page=1)

- [ ] **Develop GenAI Apps (GCP Skills Boost)**: Deploying containerized applications to the cloud. [Lab](https://www.cloudskillsboost.google/course_templates/735)

### Level 4: Kubernetes Security (CKS)

- [ ] https://tryhackme.com/room/introtocontainerisation
- [ ] https://tryhackme.com/module/kubernetes-hardening
* [ ] https://tryhackme.com/room/kubernetesforyouly
* [ ] https://tryhackme.com/room/insekube

- [ ] **Kubernetes Goat**: Simulating container escapes and cluster attacks. [Lab](https://madhuakula.com/kubernetes-goat/)

- [ ] **Network Policies (Killercoda)**: Creating "Default Deny" policies. [Laba](https://killercoda.com/killer-shell-cks/scenario/networkpolicy-create-default-deny)

- [ ] **RBAC Least Privileges (Killercoda)**: Limiting service account privileges. [Laba](https://killercoda.com/killer-shell-cks/scenario/rbac-serviceaccount-permissions)

### Level 5: LIVE Hardening and Risk Mitigation

- [ ] **Scenario "Saint John" (SadServers)**: Finding a process cluttering the disk with logs (DoS risk). [Laba](https://sadservers.com/scenarios)

- [ ] **Scenario "Bilbao" (SadServers)**: Fixing the K8s pod manifest that won't start. [Lab](https://sadservers.com/scenarios)

- [ ] **Runtime Security with Falco (Killercoda)**: LIVE monitoring of suspicious activity in containers. [Laba](https://killercoda.com/killer-shell-cks/scenario/falco-change-rule)

- [ ] **Vulnerable Lambda (CloudGoat/AWS)**: Exploiting SSRF to steal cloud secrets. [Lab](https://github.com/ine-labs/AWSGoat)


# K8S and Networks Courses & Labs
>tl;dr: read roadmap and do labs on free platforms, play games, use yandex cloud / AWS to deploy something
## K8S games

^8d161b

* [ ] https://www.k8sgames
* [ ] https://k8svisual.com
* [ ] https://learn.kodekloud.com/user/courses/kubernetes-challenges aka Game of Pods
---
## play with kubernetes
* [ ] https://training.play-with-kubernetes.com/
## Kubernetes Goat - k8s security labs
👉 https://github.com/madhuakula/kubernetes-goat
## ixumiuz
- [labs.iximiuz.com](https://labs.iximiuz.com)
## sadservers
- https://sadservers.com
### 💻 topics:
- Kubernetes misconfig
- RBAC
- container breakout

## KillerCoda
- https://killercoda.com/
## k8s learning path
- https://github.com/NotHarshhaa/kubernetes-learning-path

---

# 🧪 Cloud Security
- [ ] https://tryhackme.com/room/cloudcomputingfundamentals
- [ ] https://tryhackme.com/room/cloudsecuritypitfalls
##  Russian path - yandex courses

^9737c2

^a0b546
- [ ] https://yandex.cloud/ru/training/base/?from=training-pro
* [ ] https://yandex.cloud/ru/training/ycloud?from=training-pro
* [ ] https://yandex.cloud/ru/training/compute/?from=training-pro
* [ ] https://yandex.cloud/ru/training/kubernetes/?from=training-pro
* [ ] https://yandex.cloud/ru/training/terraform/?from=training-pro
* [ ] https://yandex.cloud/ru/training/gitlab/?from=training-pro
* [ ] https://yandex.cloud/ru/training/monitoring/?from=training-pro
* [ ] https://yandex.cloud/ru/training/infrastructure-protection?from=training-pro 
* [ ] https://yandex.cloud/ru/training/devsecops/?from=training-pro
* [ ] https://yandex.cloud/ru/training/network-security?from=training-pro
* [ ] https://yandex.cloud/ru/training/authentication?from=training-pro
* [ ] https://yandex.cloud/ru/training/appdef?from=training-pro
---
# Cloud Security - Western / international path:
## [Google Skills - hands on labs in real cloud](https://www.skills.google/catalog)

---
## 🟩 Cloud Security Labs (FREE)
👉 https://cloudlearn.io/labs

📌:
- real cloud environments
- AWS / Azure security :contentReference[oaicite:4]{index=4}
---
## ☁️ EKS cluster Game
### CTF-like challenges about cloud security in AWS EKS

* [ ] https://eksclustergames.com
---
## CloudGoat (AWS)

^885d58

- https://github.com/RhinoSecurityLabs/cloudgoat

👉 scenarios:
- IAM privilege escalation
- S3 misconfig
- SSRF → metadata

## AWSGoat
- https://github.com/ine-labs/AWSGoat

## AWS Well-Architected Labs (Security)
- https://www.wellarchitectedlabs.com/security/


## 🟪 AWS Free Tier
👉 https://aws.amazon.com/free

---

## 🟦 Haxcamp (Cloud + Security)
👉 https://haxcamp.com/projects/

### 💻 topics:
- cloud security
- AWS assessment
- misconfig

---

## 🟦 Microsoft Learn (sandbox)
👉 https://learn.microsoft.com/training


---

# ⚔️ Offensive Security Additions

## 1. Cloud Infrastructure Attacks
* [ ] **IAM Privilege Escalation**: Identifying and exploiting over-privileged roles to gain Administrator access.
* [ ] **Storage Misconfigurations**: Exploiting public S3 buckets, Azure Blobs, and Google Cloud Storage for data exfiltration.
* [ ] **Metadata Service (IMDS) Attacks**: Exploiting SSRF to steal temporary cloud credentials from the instance metadata service (v1 and v2).

## 2. Kubernetes & Container Offensive
* [ ] **K8s RBAC Exploitation**: Using service account tokens to escalate privileges within a cluster.
* [ ] **Container Breakouts**: Escalating from a container to the host node using misconfigured capabilities or kernel exploits.
* [ ] **Attacking the K8s API**: Identifying exposed Kubelets and API servers for unauthorized access.

## 3. Serverless & CI/CD Offensive
* [ ] **Attacking Lambda/Functions**: Exploiting event-driven functions to gain a foothold in the cloud environment.
* [ ] **CI/CD Pipeline Poisoning**: Exploiting GitHub Actions or GitLab CI/CD to steal secrets and inject malicious code.

---

### 📚 Learning Resources
* [**HackTricks Cloud**](https://cloud.hacktricks.xyz/) - The best free wiki for cloud exploitation techniques (AWS, Azure, GCP, Kubernetes).
* [**Prowler (Open Source)**](https://github.com/prowler-cloud/prowler) - A free tool to audit cloud security. Learn by running it and analyzing findings.
* [**CloudFox**](https://github.com/BishopFox/cloudfox) - A free tool for cloud penetration testing. Excellent for enumeration.

### 🛡️ CI/CD & DevSecOps
* [**CI/CD Goat**](https://github.com/cider-security-research/cicd-goat) - A free, self-hosted lab to learn about vulnerabilities in CI/CD pipelines (Jenkins, GitHub Actions, etc.).
