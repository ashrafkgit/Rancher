RKE Concepts

Thursday, May 4, 2023

8:03 AM

 

> **RKE Introduction**
>
>  
>
> Rancher Kubernetes Engine (RKE) is a CNCF-certified Kubernetes distribution that runs entirely within Docker containers.
>
> It works on bare-metal and virtualized servers.
>
>  
>
> Requirements:
>
> SSH Connection to the nodes
>
> Docker Installed on the nodes.
>
>  
>
>  

-   RKE uses cluster.yml config file to define the kubernetes cluster.

-   Each cluster.yml represents a kubernetes cluster configuration.

-   rke up uses the cluster.yml to get the nodes information and it installs the cluster according to the specs defined in the file.

>  
>
> Cluster.yml = **Is RKE config file**
>
>  

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>---</p>
<p>nodes:</p>
<p>- address: 10.0.0.1</p>
<p>role: [controlplane,etcd,worker]</p>
<p>user: ubuntu</p>
<p>hostname_override: node1</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

>  
>
> <https://rke.docs.rancher.com/example-yamls>
>
>  

<table>
<colgroup>
<col style="width: 72%" />
<col style="width: 27%" />
</colgroup>
<thead>
<tr class="header">
<th>$rke up --config cluster.yml</th>
<th>DEMO!!</th>
</tr>
</thead>
<tbody>
</tbody>
</table>

> * *

<table>
<colgroup>
<col style="width: 59%" />
<col style="width: 40%" />
</colgroup>
<thead>
<tr class="header">
<th>$rke config --empty --print</th>
<th>To generate new empty config file</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>$export KUBECONFIG=$PWD/kube_config_cluster.yml</td>
<td>To help communicate with the cluster</td>
</tr>
</tbody>
</table>

>  

<table>
<colgroup>
<col style="width: 85%" />
<col style="width: 14%" />
</colgroup>
<thead>
<tr class="header">
<th>Then, run $kubectl get nodes, to check the nodes status.</th>
<th> </th>
</tr>
</thead>
<tbody>
</tbody>
</table>

>  
>
>  
>
>  
>
>  
>
>  
>
> **RKE Design** - RkeConfig
>
> <span dir="rtl">-</span>
>
> The first building block of RKE is the configuration file definition which by default is called *cluster.yml*
>
> RKE config can be generated using (rke config) command.
>
>  
>
> In cluster.yml file, the nodes will represent machines and their roles where kubernetes is deployed, and whereas *services* will represent kubernetes components to be installed.
>
> * *
>
> <img src="media/image1.png" style="width:5.04167in;height:2.02083in" />
>
>  
>
>  
>
>  
>
>  
>
>  
>
> **RKE Design** - State File (cluster.rkestate)
>
>  
>
> Once the RKE installation is completed with *rke up* command using cluster.yml file, it will create a *cluster.rkestate* file
>
>  
>
> RKE uses a config file (cluster.yml) to provision cluster, and keeps track of cluster status using a state file (cluster.rkestate)
>
>  
>
> State File consists of two sections:
>
>  

-   DesiredState

-   CurrentState

>  
>
> *Desired state* represents the state the cluster should be in and *Current state* represents the actual state of the cluster
>
>  
>
> Both current and desired state consists of:
>
>  

-   RKEConfig

-   Cluster Certificate bundle

>  
>
> DesiredState is populated by **rke** from *cluster.yml* file during the provisioning workflow.
>
>  
>
> On each run RKE tries to bring the cluster to match the DesiredState and then when it succeed it writes the CurrentState.
>
>  

-   Users can edit cluster.yml file , for example add new role to the new node

-   rke init will update desired state with new node info

-   rke up will add the new role

-   when finish it will update the current state

>  
>
>  
>
> While provisioning kubernetes cluster with Rancher, RKE does not use kubeadm in the background it uses it own code written in GO lang.
>
>  
>
> Configmap of the full cluster state deployed on the kubernetes system. It is not meant to be used but as a backup stored in the cluster.
>
>  
>
> $kubectl get configmap -n kube-system | grep state
>
> *full-cluster-state*
>
>  
>
>  
>
>  
>
>  
>
> **RKE Design** - Nodes and Tunnelling
>
>  
>
> Each node should have - Docker and SSH
>
> Each node **config** should have at least the following - address, SSH user, Role
>
>  
>
>  
>
> Why SSH? Because RKE connects via SSH to each node to run containers in it, uses SSH tunnelling / ssh port forwarding to connect to the docker socket on the nodes.
>
>  
>
> RKE had an option to connect to the docker daemon on each node by allowing the docker to listen to the tcp port but this proved to be really complicated way for the users to getting started quickly with RKE, and its requires user to login to each node and configure each node with tcp port and make sure connection is secured by using TLS via SSH certificates but RKE choose to use SSH tunnel to each node then use port forwarding feature to connect to the docker socket on each node.
>
>  
>
>  
>
>  
>
> Different modes of RKE depends of the kind of tunnelling factories
>
>  
>
> RKE library , connect docker with service port or
>
>  
>
> RKE modes are:
>
>  

-   RKE cli

> \- Docker tunnel / ssh --&gt; docker.sock

-   RKE local

> \- Dokcer tunnel / ssh --&gt; docker service port

-   RKE dind

> \- Dokcer tunnel / ssh --&gt; docker service port
>
>  
>
>  
>
> Rke local - deploys k8s cluster and its components locally on the machine
>
> RKE dind (docker in docker) - creates different docker containers and specify them as nodes, deploys k8s components within docker container
>
>  
>
>  
>
>  
>
>  
>
> **RKE Design** - Services
>
>  
>
> RKE deploys k8s components as docker containers.
>
>  
>
> Components are deployed according to the node's role (different planes):
>
>  
>
>  
>
>  
>
> **Etcd**

-   etcd container

-   kube-proxy container

-   kubelet container

-   Nginx-proxy container

>  
>
> **Controlplane**

-   kube-apiserver container

-   kube-controller-manager container

-   kube-scheduler container

-   kube-proxy container

-   kubelet container

>  
>
> **Worker**

-   kube-proxy container

-   kubelet container

-   Nginx-proxy container

>  
>
> **Helper services**

-   Sidekick container (rke-tools)

-   Port check container (rke-tools)

-   Etcd recurring snapshot (rke-tools)

-   Certificate installer (rke-tools)

-   File deployer (rke-tools)

-   Addon Deployer (rke-tools) $docker ps -a | grep rke-tools

>  
>
>  
>
>  
>
>  
>
>  

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>kubelet</p>
<p> </p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

>  
>
> entrypoint.sh
>
>  

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th>Sidekick</th>
</tr>
</thead>
<tbody>
</tbody>
</table>

>  
>
>  
>
>  
>
>  
>
>  
>
> **RKE Design** - Version
>
>  

-   Each RKE version release defines kubernetes version

-   Each RKE version comes with supported kubernetes versions

> $ rke config -l -a
>
>  
>
>  
>
>  

-   Version mapping is defined in kontainer-driver-metadata repo

> <https://github.com/rancher/kontainer-driver-metadata>
>
>  

-   And each kubernetes version with mapped RKE version has different system images

-   For example :

> <img src="media/image2.jpeg" style="width:5in;height:2.5in" />
>
>  
>
>  
>
>  
>
> Earlier RKE version use to store cluster / rke state information in form of secrets on the kubernetes cluster
>
> It proved to be inconsistent while adding and removing nodes
>
> It is now stored in form of config - which can be used to reconstruct rke cluster as well.
>
>  
>
> $kubectl get configmap -n kube-system | grep state
>
> $kubectl get configmap -n kube-system full-cluster-state -o yaml (full cluster state)
>
> $kubectl get configmap -n kube-system full-cluster-state -o json | jq.data
>
>  
>
>  
>
>  
>
>  
>
>  
>
>  
>
> **RKE Provisioning** Workflow
>
>  

-   The RKE code uses 2 main functions to build cluster i ,e; **ClusterInit()** and **ClusterUp()**

> **rke init -&gt; rke up**
>
>  

-   ClusterInit is rke init which update the desire state of the **state file, which** means **ClusterInit() is** responsible for updating the DesireState and write a new **cluster.rkestate** file

>  

-   Later the cluster up compares the current state file with desired state file, if it applies difference then it applies difference on the cluster and it updates the current state with the new state of the cluster

>  
>
>  
>
>  
>
> <img src="media/image3.png" style="width:4in;height:4.15278in" />
>
>  
>
>  
>
>  
>
> <u>X509 Component Authentication</u>
>
>  

-   RKE components uses X509 Authentication

-   Generating certs works as follows:

    -   Generate master CA cert and Aggregation layer CA cert/key pair.

    -   Generate cert/key pair for each service (kube-api, scheduler, controller, kubelet, kube-proxy)

    -   Generate etcd cert/key pair for each etcd node.

    -   Generate proxy-client cert/key pair.

    -   Generate service account key file.

>  

-   On each rke run, rke checks if etcd/cp node is added or removed, if yes then:

> It generates etcd/kube-api cert for each new node
>
> It regenerates old etcd/kube-api cert to update the SANS
>
>  

-   Certificate rotation happens in rke init, it regenerates all certs.

>  
>
>  
>
> <img src="media/image4.png" style="width:3.16667in;height:2.3125in" />
>
>  
>
>  
>
> Kubelet has its own api certificate which API has to authenticate with kubelet api server
>
>  
>
>  
>
>  
>
>  
>
> **RKE Reconciliation loop** ( ADD/REMOVE cycle)
>
>  
>
> <u>Removing a node</u>
>
>  

-   RKE first checks for the ROLE:

> If node is part of ETCD

-   Removes etcd member from etcd cluster ( etcdctl member remove)

-   Delete the node from K8s cluster ( kubectl delete node &lt;&gt;)

-   Clean the docker containers on the host

> If node is CP/Worker node:

-   Delete the node from K8s cluster ( kubectl delete node &lt;&gt; )

-   Clean the docker containers on the host

>  
>
> <u>Adding a node</u>
>
>  

-   RKE first checks for the ROLE:

> If it is ETCD node and not already a member

-   Add ETCD member to the cluster ( etcdctl member remove)

-   Run ETDC on the new node

> If node is CP/Worker:

-   Sync taints

>  
>
>  
>
> Important notes:-
>
>  
>
>  

-   To use new features RKE cluster must be upgraded ( to upgrade to specific version, define version in the cluster.yaml file)

>  

-   Can multiple ETCDs be removed ? Yes , yes remove nodes from the yaml file and reconciling loop should delete one by one without breaking cluster

>  

-   How RKE is using certificates for worker nodes,

>  
>
> All nodes use the same client certificate to allow Kubelet to reach the Kubernetes API server, which is not that good for security
>
> Kubelet uses a self-signed certificate for its HTTPS endpoint, instefad of using a certificated generated by the Kubernetes CA.
>
>  
>
> After reading "Kubernetes The Hard Way" by Kelsey Hightower:
>
>  
>
> It confirms that having one certificate for Kubelet for each worker node is the best practice:
>
> <https://github.com/kelseyhightower/kubernetes-the-hard-way/blob/master/docs/04-certificate-authority.md#the-kubelet-client-certificates>
>
> Using that certificate and the associated key for Kubelet HTTPS is also what is done (through Kubelet tlsCertFile and tlsPrivateKeyFile options):
>
> <https://github.com/kelseyhightower/kubernetes-the-hard-way/blob/master/docs/09-bootstrapping-kubernetes-workers.md#configure-the-kubelet>
>
> We can also notice that the certificate generated includes the IP address i'm looking for.
>
> For RKE, it should correspond to the node "address" and the node "internal\_address" defined in the YAML cluster file.
>
>  
>
> This is solved by using the configuration in [rancher/rancher#15793 (comment)](https://github.com/rancher/rancher/issues/15793#issuecomment-602049405)
>
> Docs:  <https://rancher.com/docs/rke/latest/en/config-options/services/#kubelet>
>
> * *
>
>  
>
>  
>
>  
>
>  
>
>  
>
>  
>
>  