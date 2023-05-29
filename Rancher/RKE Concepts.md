## RKE Concepts

**RKE Introduction**
##
Rancher Kubernetes Engine (RKE) is a CNCF-certified Kubernetes distribution that runs entirely within Docker containers.

It works on bare-metal and virtualized servers.

_Basic requirements:_

> SSH Connection to the nodes.

> Docker Installed on the nodes.

  

- RKE uses cluster.yml config file to define the kubernetes cluster.
- Each cluster.yml represents a kubernetes cluster configuration.
- rke up uses the cluster.yml to get the nodes information and it installs the cluster according to the specs defined in the file.

  

 Cluster.yml = **Is RKE config file**

  
``` bash
---
nodes:
     -  address: 10.0.0.1 
         role: [controlplane,etcd,worker] 
         user: ubuntu
         hostname_override: node1
```

https://rke.docs.rancher.com/example-yamls

  
_Demo!!_
``` bash
$rke up --config cluster.yml
```

_To generate new empty config file_
```bash
$rke config --empty --print
```

_To help communicate with the cluster_
``` bash
$export KUBECONFIG=$PWD/kube_config_cluster.yml
```

Then, run $kubectl get nodes, to check the nodes status.







##
## RKE Design

**RKE Design** - RKEConfig
##
The first building block of RKE is the configuration file definition which by default is called *cluster.yml*

RKE config can be generated using (rke config) command.

In cluster.yml file, the nodes will represent machines and their roles where kubernetes is deployed, and whereas *services* will represent kubernetes components to be installed.

![image](https://github.com/ashrafkgit/Rancher/assets/134578702/3655c7ee-593c-43c0-bc0b-82a13a506f27)





##
**RKE Design** - State File (cluster.rkestate)
##
Once the RKE installation is completed with *rke up* command using cluster.yml file, it will create a *cluster.rkestate* file

RKE uses a config file (cluster.yml) to provision cluster, and keeps track of cluster status using a state file (cluster.rkestate)

State File consists of two sections:

- DesiredState
- CurrentState
 

*Desired state* represents the state the cluster should be in and *Current state* represents the actual state of the cluster.

Both current and desired state consists of:
- RKEConfig
- Cluster Certificate bundle
 

DesiredState is populated by **rke** from *cluster.yml* file during the provisioning workflow.

On each run RKE tries to bring the cluster to match the DesiredState and then when it succeed it writes the CurrentState.

-   Users can edit cluster.yml file , for example add new role to the new node

-   rke init will update desired state with new node info

-   rke up will add the new role

-   when finish it will update the current state

  
While provisioning kubernetes cluster with Rancher, RKE does not use kubeadm in the background it uses it own code written in GO lang.

Configmap of the full cluster state deployed on the kubernetes system. It is not meant to be used but as a backup stored in the cluster.





_Get full-cluster-state by cmd_
``` bash

$kubectl get configmap -n kube-system | grep state

```


  

  
##
**RKE Design** - Nodes and Tunnelling
##
 

Each node should have - Docker and SSH

Each node **config** should have at least the following - address, SSH user, Role

  

_Notes:
Why SSH? Because RKE connects via SSH to each node to run containers in it, uses SSH tunnelling / ssh port forwarding to connect to the docker socket on the nodes.

RKE had an option to connect to the docker daemon on each node by allowing the docker to listen to the tcp port but this proved to be really complicated way for the users to getting started quickly with RKE, and its requires user to login to each node and configure each node with tcp port and make sure connection is secured by using TLS via SSH certificates but RKE choose to use SSH tunnel to each node then use port forwarding feature to connect to the docker socket on each node._


  
Different modes of RKE depends of the kind of tunnelling factories
 

RKE library , connect docker with service port or

RKE modes are:

- RKE cli
 
  Docker tunnel / ssh --&gt; docker.sock
  
  
- RKE local
  
  Dokcer tunnel / ssh --&gt; docker service port
  
  
- RKE dind
  
  Dokcer tunnel / ssh --&gt; docker service port
 

 

RKE local - deploys k8s cluster and its components locally on the machine

RKE dind (docker in docker) - creates different docker containers and specify them as nodes, deploys k8s components within docker container

 
##
**RKE Design** - Services
##
 

RKE deploys k8s components as docker containers.

Components are deployed according to the node's role (different planes):

 **Etcd**

- etcd container
- kube-proxy container
- kubelet container
- Nginx-proxy container


**Controlplane**

- kube-apiserver container
- kube-controller-manager container
- kube-scheduler container
- kube-proxy container
- kubelet container

**Worker**

- kube-proxy container
- kubelet container
- Nginx-proxy container

**Helper services**

- Sidekick container (rke-tools)
- Port check container (rke-tools)
- Etcd recurring snapshot (rke-tools)
- Certificate installer (rke-tools)
- File deployer (rke-tools)
- Addon Deployer (rke-tools) 


_To get rke-tools process status_
``` bash
$docker ps -a | grep rke-tools
```

![image](https://github.com/ashrafkgit/Rancher/assets/134578702/c2b099a7-494b-4bed-be4d-1338715f3e36)




##
**RKE Design** - Version
##
 
 - Each RKE version release defines kubernetes version
 - Each RKE version comes with supported kubernetes versions

``` bash 
$ rke config -l -a
```

- Version mapping is defined in kontainer-driver-metadata repo
  
    https://github.com/rancher/kontainer-driver-metadata>
   
- And each kubernetes version with mapped RKE version has different system images

For example:
![image](https://github.com/ashrafkgit/Rancher/assets/134578702/547c051d-3886-4492-8439-3316d135fb2d)


Earlier RKE version use to store cluster / rke state information in form of secrets on the kubernetes cluster proved to be inconsistent while adding and removing nodes.
It is now stored in form of config - which can be used to reconstruct rke cluster as well.

``` bash
$kubectl get configmap -n kube-system | grep state
```

_fetch full cluster state_
``` bash
$kubectl get configmap -n kube-system full-cluster-state -o yaml 
```
``` bash
$kubectl get configmap -n kube-system full-cluster-state -o json | jq.data
```


##
**RKE Provisioning** Workflow
##
 
The RKE code uses 2 main functions to build cluster i ,e; **ClusterInit()** and **ClusterUp()**

**rke init -&gt; rke up**

- ClusterInit is rke init which update the desire state of the **state file, which** means **ClusterInit() is** responsible for updating the DesireState and write a new **cluster.rkestate** file
- Later the cluster up compares the current state file with desired state file, if it applies difference then it applies difference on the cluster and it updates the current state with the new state of the cluster

![image](https://github.com/ashrafkgit/Rancher/assets/134578702/7c5cdc18-190e-4e8d-9678-9139d5a3f6a9)


##
## X509 Component Authentication
##

- RKE components uses X509 Authentication
- Generating certs works as follows:

    > Generate master CA cert and Aggregation layer CA cert/key pair.
    
    > Generate cert/key pair for each service (kube-api, scheduler, controller, kubelet, kube-proxy)
    
    > Generate etcd cert/key pair for each etcd node.
    
    > Generate proxy-client cert/key pair.
    
    > Generate service account key file.



- On each rke run, rke checks if etcd/cp node is added or removed, if yes then:

    > It generates etcd/kube-api cert for each new node
    
    > It regenerates old etcd/kube-api cert to update the SANS

- Certificate rotation happens in rke init, it regenerates all certs.

![image](https://github.com/ashrafkgit/Rancher/assets/134578702/48964b9b-b771-4f8d-be6d-c7d4338540ac)

_Kubelet has its own api certificate which API has to authenticate with kubelet api server_


##
**RKE Reconciliation loop** ( ADD/REMOVE cycle)
##


**Removing a node**  

RKE first checks for the ROLE:

_If node is part of ETCD_

> Removes etcd member from etcd cluster ( etcdctl member remove)
\ 
> Delete the node from K8s cluster ( kubectl delete node <>)

> Clean the docker containers on the host

_If node is CP/Worker node_

> Delete the node from K8s cluster ( kubectl delete node <>)

> Clean the docker containers on the host



**Adding a node**

RKE first checks for the ROLE:

_If it is ETCD node and not already a member_

> Add ETCD member to the cluster ( etcdctl member remove)

> Run ETDC on the new node

_If node is CP/Worker_

> Sync taints
> 
> 
> 
> 
> 
##
##
**_Important notes_**
##
##

- To use new features RKE cluster must be upgraded ( to upgrade to specific version, define version in the cluster.yaml file)

- Can multiple ETCDs be removed ? Yes , yes remove nodes from the yaml file and reconciling loop should delete one by one without breaking cluster

- How RKE is using certificates for worker nodes,

     > All nodes use the same client certificate to allow Kubelet to reach the Kubernetes API server, which is not that good for security
      
     > Kubelet uses a self-signed certificate for its HTTPS endpoint, instefad of using a certificated generated by the Kubernetes CA.



After reading "Kubernetes The Hard Way" by Kelsey Hightower:

It confirms that having one certificate for Kubelet for each worker node is the best practice:

https://github.com/kelseyhightower/kubernetes-the-hard-way/blob/master/docs/04-certificate-authority.md#the-kubelet-client-certificates

Using that certificate and the associated key for Kubelet HTTPS is also what is done (through Kubelet tlsCertFile and tlsPrivateKeyFile options):

https://github.com/kelseyhightower/kubernetes-the-hard-way/blob/master/docs/09-bootstrapping-kubernetes-workers.md#configure-the-kubelet

We can also notice that the certificate generated includes the IP address i'm looking for. 

For RKE, it should correspond to the node "address" and the node "internal_address" defined in the YAML cluster file.

This is solved by using the configuration in rancher/rancher#15793 (comment)

Docs:  https://rancher.com/docs/rke/latest/en/config-options/services/#kubelet






