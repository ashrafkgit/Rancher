##
## Understanding Cluster Configuration 
##

 <img src="media/image1.png" style="width:8.27778in;height:2.79167in" /

  

 <img src="media/image2.png" style="width:4.5in;height:5.1875in" /

  

  

  

  

  

  

  

  

 **Adding a node to a customer cluster**

  

  

 <img src="media/image3.png" style="width:6.5in;height:1.90278in" /

  

  

  

 Find all options in the documentation

 <https://ranchermanager.docs.rancher.com/v2.5/reference-guides/cluster-configuration/rancher-server-configuration/use-existing-nodes/rancher-agent-options

  

  

 The Rancher agent is used to add a node to a cluster, and provide connectivity from Rancher to the node to provision/reconcile the node according to the cluster configuration

  

 After the node is successfully registered to the cluster (after provisioning has been completed and the kubelet was started and successfully connected to the kube-apiserver),

 the agent container created via the docker run command is removed by the cattle-node-agent DaemonSet pods

  

 More information about the agents is in the documentation:

 <https://rancher.com/docs/rancher/v2.x/en/cluster-provisioning/rancher-agents/

  

  

  

  

  

 **Global flow of agent while adding a node**

  

 Global flow of agent:

  

 1\. Launch agent container

 2\. Entrypoint is a shell script which parses the flags and runs some validation tests on the flags and provided values (¹)

 3\. Runs agent binary and connects to Rancher using a WebSocket connection (2)

 4\. Validate cluster and token, create node (3)

 5\. Agent executes the plan provided by Rancher (4)

 6\. Rancher will run cluster provisioning/reconcile based on a new node being added

 7\. Node will be registering to the cluster and the cattle-node-agent DaemonSet pods will remove any agent container that was run via the provided Docker run command (5)

  

 1\. <https://github.com/rancher/rancher/blob/v2.3.3/package/run.sh

 2\. <https://github.com/rancher/rancher/blob/v2.3.3/pkg/agent/main.go#L265

 3\. <https://github.com/rancher/rancher/blob/v2.3.3/pkg/tunnelserver/tunnel.go#L107

 4\. <https://github.com/rancher/rancher/blob/v2.3.3/pkg/rkenodeconfigclient/client.go#L68

 5\. <https://github.com/rancher/rancher/blob/v2.3.3/pkg/agent/main.go#L277

  

  

  

 **Custom cluster provisioning/reconcile**

-   All clusters in Rancher are configured with a *driver* (look for the \`driver\` key in the View in API view for a cluster)

-   The term kontainerdriver refers to kontainer-engine (<https://github.com/rancher/kontainer-engine), which is a command line tool and used as a library in Rancher to provision clusters

-   Kontainer-engine uses drivers as well, a driver contains the logic to *create/update/remove clusters* (¹)

-   See the functions Create/Update/Remove for the most common cluster actions, here you can also find the reference to the RKE functions.


-  For instance, when an update to the cluster is called (2)

  https://github.com/rancher/kontainer-engine/blob/master/drivers/rke/rke_driver.go

  https://github.com/rancher/kontainer-engine/blob/release/v2.3/drivers/rke/rke_driver.go#L229

  

-   Rancher uses Kubernetes controllers to make sure certain actions regarding clusters can be performed

-   Kubernetes controllers are control loops that watch a state and act upon them (bring current state to desired state)

  

-   There are many controllers in Rancher, below are controllers mentioned that are a good starting point

  

-   The *cluster provisioner controlle*r kicks off the needed functions to provision/reconcile a cluster (')

-   The *nodesyncer* makes sure the node in Rancher is synced with its state in Kubernetes (amongst other functions like labels and deleting the node if its deleted on the Kubernetes side) (2)

  

 1\. <https://github.com/rancher/rancher/blob/v2.3.3/pkg/controllers/management/clusterprovisioner/provisioner.go#L388

 2\. <https://github.com/rancher/rancher/blob/v2.3.3/pkg/controllers/user/nodesyncer/nodessyncer.go#L218

  

  

  

 **Rancher and worker nodes**

  

-   Worker nodes are handled differently in Rancher, they are not part of the provisioning/reconcile process (The banner in Rancher indicating a cluster is in Provisioning state)

-   Agent requests nodeconfig, nodeconfig is generated on Rancher side, agent executes the nodeconfig (¹)

-   The nodeconfig consists of everything needed for the Kubernetes components to function

    -   What Docker containers need to be running for each Kubernetes component

    -   What configuration is needed for each Kubernetes component

    -   Any files needed to configure each Kubernetes component (For example, cloud-config, but also certificates)

  

-  https://github.com/rancher/rancher/blob/v2.3.3/pkg/rkeworker/execute.go

  

  

 Provisioning state will process nodes with the roles etcd and/or Control Plane, as cluster provisioning succeeds, the workers will execute the contents of their own retrieved nodeconfig

  

  

 <img src="media/image4.png" style="width:4.5625in;height:2.79167in" /

  

  

 docker exec $(docker ps --filter-label-io.cattle.agent-true --filter-name-node-agent-format='{{.ID}}') bash -c 'PARAMS=$(echo \\Node\\:{\\requestedHostname\\:\\$(echo SCATTLE\_NODE\_NAME)\\}} | base64 -w8); curl -s -k -H "X-API-Tunnel-Token: $(cat /cattle-credentials/token)" -H "X-Api-Tunnel-Params: "$(echo $PARAMS)" "$(cat /cattle-credentials/url)/v3/connect/config" ' jq . | less

  

  

 Endpoint used in command: /cattle-credentials/url)/v3/connect/config

 Output list: cluster name, certificates thats provisioned and needs for cluster communication, Image of rancher, entrypoint, sidekicks

 Information create from rancher side and RKE side as well ( configuration that is built during provisioning process against the nodes)

  

  

  

 **ETCD Snapshots**

  

  

-   In RKE, etcd snapshots are handled by creating the etcd-rolling-snapshots container with the configuration as defined in cluster.yml

-   When provisioning a custom cluster via Rancher, this container does not exist

-   Rancher is responsible for creating/rotating/deleting etcd snapshots for custom clusters

-   This is handled by a controller, the *etcdbackup-controller* (')

  

 1.https://github.com/rancher/rancher/blob/v2.3.3/pkg/controllers/management/etcdbackup/etcdbackup.go

  

  

 By default, etcd data is stored under local host filesystem not container filesystem

 RKE Container engine is written in Golang, all rancher Golang libraries are written in Go Lang and interactions to other clusters GKE/AKS/EKS ( all have Golang libraries)happens with the help of Go lang libraries and functions to make sure provisioning works. ( Google VMs have known issues with ssh/authentication for the provisioning of cluster, a bug is opened)

  

  

 GKE

  

  
