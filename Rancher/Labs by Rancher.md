##
## Labs by Rancher
##


 

In-depth online workshop designed to give DevOps and IT teams the hands-on skills they need to deploy and manage Kubernetes everywhere.


Rancher Rodeo XIV - 2.7

 

 

![image](https://github.com/ashrafkgit/Rancher/assets/134578702/42c97397-88b9-4a0e-9005-8d78c7d32044)

 

![image](https://github.com/ashrafkgit/Rancher/assets/134578702/1dee8179-ca87-48c0-91b2-cfb57182f888)

 

 

![image](https://github.com/ashrafkgit/Rancher/assets/134578702/d50cba1b-aa07-4746-973c-9b8a84fc9357)

Cffb9dnzw7sbf745jqn4n5kcls799r4ppkfv624gjlx5mh2j4lcq72

 



 

![image](https://github.com/ashrafkgit/Rancher/assets/134578702/545fa19d-9dc8-44ef-a252-d84b30fab669)

 

rr@123456789

 

 

![image](https://github.com/ashrafkgit/Rancher/assets/134578702/468740cd-11a0-4bdd-8093-5ece4a7709da)

 

[High Availability (HA) Install](https://ranchermanager.docs.rancher.com/v2.5/pages-for-subheaders/install-upgrade-on-a-kubernetes-cluster)

 

 

![image](https://github.com/ashrafkgit/Rancher/assets/134578702/c4d8cf9d-6d06-463e-a1f0-ae0177e8a9a5)
![image](https://github.com/ashrafkgit/Rancher/assets/134578702/2db413c6-98ad-45b2-939f-62f6496c52ee)

 

[RKE2 Documentation](https://docs.rke2.io/)

 

 

 

![image](https://github.com/ashrafkgit/Rancher/assets/134578702/fbbe6fd4-e692-434b-ade1-dbabc19cca20)

 

![image](https://github.com/ashrafkgit/Rancher/assets/134578702/26310467-f950-4a9f-90b0-c9f03ebcdc78)

 

![image](https://github.com/ashrafkgit/Rancher/assets/134578702/6f2349a5-1769-483b-9826-982a7a67e862)



 

![image](https://github.com/ashrafkgit/Rancher/assets/134578702/75ebe9dc-eaa6-452c-b639-a813ec8549f2)

 

![image](https://github.com/ashrafkgit/Rancher/assets/134578702/2d12caf7-1d00-4e15-a1af-7c1d1ec11233)

 

 

![image](https://github.com/ashrafkgit/Rancher/assets/134578702/3e8e71e6-41cd-4023-b93b-8e4502f75d66)

 

![image](https://github.com/ashrafkgit/Rancher/assets/134578702/f227e0bc-1004-4b11-996d-ce60bc4721eb)

 

![image](https://github.com/ashrafkgit/Rancher/assets/134578702/df16dc32-61d7-47e2-b7fb-d65a864f591a)

 

![image](https://github.com/ashrafkgit/Rancher/assets/134578702/93ce3b1d-9c81-452d-bd6a-c7d8246dfaff)

 

 

<img src="media/image17.png" style="width:12.68056in;height:6.75in" />

 

 

 

<img src="media/image18.png" style="width:13.32639in;height:5.69444in" />

 

<img src="media/image19.png" style="width:13.27778in;height:2.49306in" />

 

 

 

 

 

<img src="media/image20.png" style="width:13.32639in;height:6.40278in" />

 

 

<img src="media/image21.png" style="width:13.3125in;height:6.17361in" />

 

<img src="media/image22.png" style="width:13.29167in;height:4.6875in" />

 

 

 

 

 

 

<img src="media/image23.png" style="width:13.32639in;height:6.34722in" />

 

 

 

 

** Rancher Kubernetes Cluster Bootstrapping**

 

ec2-user@ip-172-31-44-121:~&gt; curl -fL <https://rancher.34.242.237.239.sslip.io/system-agent-install.sh> | sudo sh -s - --server <https://rancher.34.242.237.239.sslip.io> --label 'cattle.io/os=linux' --token cf55b9n5bcwtd4zzqgsdgfsz7xv78246gzzsrm9nqz5nq6frg4wrsf --ca-checksum e5b2f4cc07660772707d3c35a83e6f7c180f5a97301aa9e63282ac2e7b545262 --etcd --controlplane --worker --node-name cluster01

 

* *

* *

<img src="media/image24.png" style="width:13.32639in;height:6.34722in" />

 

 

<img src="media/image25.png" style="width:13.32639in;height:6.4375in" />

 

 

<img src="media/image26.png" style="width:13.32639in;height:6.375in" />

 

 

 

Downloaded KUBE CONFIG File

 

&lt;&lt;cluster01.yaml&gt;&gt;

 

 

 

 

<img src="media/image27.png" style="width:13.3125in;height:5.77778in" />

 

 

&lt;&lt;cluster01.yaml&gt;&gt;

 

 

**Rancher Management Server config:-**

 

 

&lt;&lt;rancher01.txt&gt;&gt;

 

**KubeConfig:-**

 

 

&lt;&lt;Copy KubeConfig to Clipboard.txt&gt;&gt;

 

 

**Rancher Kubernetes Cluster config:-**

 

&lt;&lt;cluster01.txt&gt;&gt;

 

 

 

 

<img src="media/image28.png" style="width:13.27083in;height:5.71528in" />

 

 

 

<img src="media/image29.png" style="width:13.32639in;height:6.33333in" />

 

 

 

<img src="media/image30.png" style="width:13.32639in;height:6.40278in" />

 

 

<img src="media/image31.png" style="width:13.32639in;height:6.41667in" />

 

 

<img src="media/image32.png" style="width:13.29861in;height:6.38194in" />

 

 

<img src="media/image33.png" style="width:13.29167in;height:6.4375in" />

 

<img src="media/image34.png" style="width:13.29167in;height:6.39583in" />

 

 

Downloaded File

&lt;&lt;helm-operation-l76q6\_undefined.log&gt;&gt;

 

 

 

 

<img src="media/image35.png" style="width:13.3125in;height:6.39583in" />

 

<img src="media/image36.png" style="width:13.3125in;height:6.375in" />

 

<img src="media/image37.png" style="width:13.29167in;height:6.77778in" />

 

 

<img src="media/image38.png" style="width:13.32639in;height:6.30556in" />

 

<img src="media/image39.png" style="width:13.3125in;height:1.58333in" />

 

 

<img src="media/image40.png" style="width:13.27778in;height:5.6875in" />

 

<img src="media/image41.png" style="width:13.32639in;height:1.625in" />

> <img src="media/image42.png" style="width:11.35417in;height:5.10417in" />

<img src="media/image43.png" style="width:13.32639in;height:1.9375in" />

 

 

<img src="media/image44.png" style="width:13.32639in;height:6.17361in" />

 

<img src="media/image45.png" style="width:13.3125in;height:6.39583in" />

 

<img src="media/image46.png" style="width:13.32639in;height:6.35417in" />

 

 

 

<img src="media/image47.png" style="width:13.29861in;height:6.36806in" />

 

<img src="media/image48.png" style="width:13.32639in;height:6.41667in" />

 

<img src="media/image49.png" style="width:13.32639in;height:6.35417in" />

 

 

 

 

<img src="media/image50.png" style="width:13.29167in;height:6.375in" />

 

 

<img src="media/image51.png" style="width:13.3125in;height:6.38194in" />

 

<img src="media/image52.png" style="width:13.29861in;height:6.41667in" />

 

<img src="media/image53.png" style="width:13.3125in;height:6.30556in" />

 

 

 

<img src="media/image54.png" style="width:13.32639in;height:6.33333in" />

 

 

<img src="media/image55.png" style="width:13.29861in;height:6.45833in" />

 

 

<img src="media/image56.png" style="width:13.32639in;height:6.375in" />

 

 

 

<img src="media/image57.png" style="width:13.29167in;height:5.95833in" />

 

<img src="media/image58.png" style="width:13.23611in;height:6.42361in" />

 

<img src="media/image59.png" style="width:13.32639in;height:6.40278in" />

 

 

<img src="media/image60.png" style="width:13.32639in;height:6.38194in" />

 

 

Downloaded file

 

&lt;&lt;helm-operation-clprm\_undefined.log&gt;&gt;

 

 

<img src="media/image61.png" style="width:13.29167in;height:6.375in" />

 
