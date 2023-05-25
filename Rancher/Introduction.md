## Introduction

**Rancher** - An open source management tool (to unlock full potential of K8s)

-Monitor health of all K8 clusters through single pane of glass.

-Simplify and automate the management of containerized applications.

-Deploy persistent storage at one click and simplify RBAC and security, which means deploy security policies from single place for the kubernetes clusters 
	
For example, you can:
  
• Use your Active Directory credentials to access Kubernetes clusters hosted by cloud vendors, such as GKE.
  
• Setup and enforce access control and security policies across all users, groups, projects, clusters, and clouds.
	
• View the health and capacity of your Kubernetes clusters from a single-pane-of-glass.

-Can integrate popular open source tools, like Prometheus, Grafana, Helm, CIS Security Scanner 

The following figure illustrates the role Rancher plays in IT and DevOps organizations. Each team deploys their applications on the public or private clouds they choose. 

IT administrators gain visibility and enforce policies across all users, clusters, and clouds.

![image](https://github.com/ashrafkgit/Linux/assets/134578702/8a86606a-3f52-4d65-866a-1d3a1a1ee234)

## Operational Challenges  (with kubernetes) 

• With so many ways to deploy, how do I deploy consistently across different infrastructures?

• How do I implement and manage access control across multiple clusters (and namespaces)

• How do I integrate with a central authentication system?

• How do I partition clusters to more efficiently use my resources?

• How do I manage multi-tenancy, multiple dedicated and shared clusters?

• How do i make my clusters highly available?

• Ensure that security policies are enforced across clusters/namespaces

• Monitoring - Do I have sufficient visibility to detect and to troubleshoot issues?


![image](https://github.com/ashrafkgit/Rancher/assets/134578702/17639af9-3364-46d5-89ae-ae4ff5a1b240)




**Two ways to install Rancher:

Sandbox - Standalone Docker Container ( not for production) & High Availability Rancher 
Single node HA Installation - if you don’t want to allow more than 2 kubernetes nodes to run Rancher 

