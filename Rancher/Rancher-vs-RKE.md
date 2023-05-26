	
  ## Rancher vs RKE 

→ Rancher is software to create and manage your Kubernetes cluster(s), including UI, central authentication, logging, monitoring, service mesh and much more
	
→ Regarding clusters, Rancher supports any Kubernetes cluster which can be added to Rancher in different ways:

* Import existing cluster by launching needed resources to manage the cluster (Rancher agents)
 
* Create a hosted Kubernetes cluster (for example, GKE (Google), AKS (Azure), EKS (AWS))
 

 
 
 ![image](https://github.com/ashrafkgit/Rancher/assets/134578702/90737ad8-7d7e-4527-aea0-b4035e99db71)
 

* Create a custom cluster (uses parts of RKE, but there are differences)


![image](https://github.com/ashrafkgit/Rancher/assets/134578702/5d46f1ce-8ede-45b0-87b9-633576144db8)

 
RKE can be installed and configured on the existing linux nodes / approach cloud provider to provision, install & configure 

 https://www.suse.com/c/rancher_blog/rancher-vs-rke-what-is-the-difference/
		
Main differences when creating a custom cluster in Rancher vs creating a cluster using RKE
		
- Custom cluster configuration is a combination of Rancher options plus RKE cluster.yml options vs just cluster.yml 
   when using RKE Nodes are dynamically added to the cluster via Rancher (agent) versus a static cluster.yml file when using RKE
 
- Only nodes with etcd and/or controlplane role are part of the RKE plan when provisioning a cluster, workers are handled by Rancher separately

- Cluster provisioning/reconcile is handled by Rancher vs rke up on the command line using RKE 

- etcd snapshots are handled by Rancher vs the etcd-rolling-snapshots-container in RKE

