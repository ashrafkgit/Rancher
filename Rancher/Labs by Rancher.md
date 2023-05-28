**Labs by Rancher**

Wednesday, May 24, 2023

8:10 AM

 

In-depth online workshop designed to give DevOps and IT teams the hands-on skills they need to deploy and manage Kubernetes everywhere.

 

<https://learn.eu.hobbyfarm.io/app/home>

 

ashraf@hpe.com

Password: rr@123

Access Code anz240523

Rancher Rodeo XIV - 2.7

 

 

<img src="media/image1.png" style="width:12.66667in;height:6.52778in" />

 

<img src="media/image2.png" style="width:9.59722in;height:5.14583in" />

 

 

<img src="media/image3.png" style="width:4.8125in;height:4.58333in" />

 

Cffb9dnzw7sbf745jqn4n5kcls799r4ppkfv624gjlx5mh2j4lcq72

 

<img src="media/image4.png" style="width:4.8125in;height:3.26389in" />

 

rr@123456789

 

 

<img src="media/image5.png" style="width:12.625in;height:7.125in" />

 

[High Availability (HA) Install](https://ranchermanager.docs.rancher.com/v2.5/pages-for-subheaders/install-upgrade-on-a-kubernetes-cluster)

 

 

<img src="media/image6.png" style="width:12.70139in;height:6.52778in" />

 

<img src="media/image7.png" style="width:12.66667in;height:2.93056in" />

 

[RKE2 Documentation](https://docs.rke2.io/)

 

 

 

<img src="media/image8.png" style="width:12.64583in;height:6.72222in" />

 

<img src="media/image9.png" style="width:12.625in;height:2.13889in" />

 

<img src="media/image10.png" style="width:12.64583in;height:6.70833in" />

\\

 

<img src="media/image11.png" style="width:12.57639in;height:6.5in" />

 

<img src="media/image12.png" style="width:12.50694in;height:3.16667in" />

 

 

<img src="media/image13.png" style="width:12.65972in;height:5.99306in" />

 

<img src="media/image14.png" style="width:12.65972in;height:6.52778in" />

 

<img src="media/image15.png" style="width:12.64583in;height:6.66667in" />

 

<img src="media/image16.png" style="width:12.70833in;height:7.13194in" />

 

 

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

 
