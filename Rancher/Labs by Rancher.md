**Labs by Rancher** 

Wednesday, May 24, 2023

8:10 AM



In-depth online workshop designed to give DevOps and IT teams the hands-on skills they need to deploy and manage Kubernetes everywhere.



<https://learn.eu.hobbyfarm.io/app/home>



ashraf@hpe.com

Password: rr@123

Access Code anz240523

Rancher Rodeo XIV - 2.7





![](Aspose.Words.6d1da65b-4d1c-4460-859c-120cd6b26b9c.001.png)



![](Aspose.Words.6d1da65b-4d1c-4460-859c-120cd6b26b9c.002.png)





![](Aspose.Words.6d1da65b-4d1c-4460-859c-120cd6b26b9c.003.png)



Cffb9dnzw7sbf745jqn4n5kcls799r4ppkfv624gjlx5mh2j4lcq72



![](Aspose.Words.6d1da65b-4d1c-4460-859c-120cd6b26b9c.004.png)



rr@123456789





![](Aspose.Words.6d1da65b-4d1c-4460-859c-120cd6b26b9c.005.png)



[High Availability (HA) Install](https://ranchermanager.docs.rancher.com/v2.5/pages-for-subheaders/install-upgrade-on-a-kubernetes-cluster)





![](Aspose.Words.6d1da65b-4d1c-4460-859c-120cd6b26b9c.006.png)



![](Aspose.Words.6d1da65b-4d1c-4460-859c-120cd6b26b9c.007.png)



[RKE2 Documentation](https://docs.rke2.io/)







![](Aspose.Words.6d1da65b-4d1c-4460-859c-120cd6b26b9c.008.png)



![](Aspose.Words.6d1da65b-4d1c-4460-859c-120cd6b26b9c.009.png)



![](Aspose.Words.6d1da65b-4d1c-4460-859c-120cd6b26b9c.010.png)

\



![](Aspose.Words.6d1da65b-4d1c-4460-859c-120cd6b26b9c.011.png)



![](Aspose.Words.6d1da65b-4d1c-4460-859c-120cd6b26b9c.012.png)





![](Aspose.Words.6d1da65b-4d1c-4460-859c-120cd6b26b9c.013.png)



![](Aspose.Words.6d1da65b-4d1c-4460-859c-120cd6b26b9c.014.png)



![](Aspose.Words.6d1da65b-4d1c-4460-859c-120cd6b26b9c.015.png)



![](Aspose.Words.6d1da65b-4d1c-4460-859c-120cd6b26b9c.016.png)





![](Aspose.Words.6d1da65b-4d1c-4460-859c-120cd6b26b9c.017.png)







![](Aspose.Words.6d1da65b-4d1c-4460-859c-120cd6b26b9c.018.png)



![](Aspose.Words.6d1da65b-4d1c-4460-859c-120cd6b26b9c.019.png)











![](Aspose.Words.6d1da65b-4d1c-4460-859c-120cd6b26b9c.020.png)





![](Aspose.Words.6d1da65b-4d1c-4460-859c-120cd6b26b9c.021.png)



![](Aspose.Words.6d1da65b-4d1c-4460-859c-120cd6b26b9c.022.png)













![](Aspose.Words.6d1da65b-4d1c-4460-859c-120cd6b26b9c.023.png)









` `**Rancher Kubernetes Cluster Bootstrapping**



ec2-user@ip-172-31-44-121:~> curl -fL <https://rancher.34.242.237.239.sslip.io/system-agent-install.sh> | sudo  sh -s - --server <https://rancher.34.242.237.239.sslip.io> --label 'cattle.io/os=linux' --token cf55b9n5bcwtd4zzqgsdgfsz7xv78246gzzsrm9nqz5nq6frg4wrsf --ca-checksum e5b2f4cc07660772707d3c35a83e6f7c180f5a97301aa9e63282ac2e7b545262 --etcd --controlplane --worker --node-name cluster01 


\*

\*


![](Aspose.Words.6d1da65b-4d1c-4460-859c-120cd6b26b9c.024.png)





![](Aspose.Words.6d1da65b-4d1c-4460-859c-120cd6b26b9c.025.png)





![](Aspose.Words.6d1da65b-4d1c-4460-859c-120cd6b26b9c.026.png)







Downloaded KUBE CONFIG File



<<cluster01.yaml>>









![](Aspose.Words.6d1da65b-4d1c-4460-859c-120cd6b26b9c.027.png)





<<cluster01.yaml>>





**Rancher Management Server config:-**





<<rancher01.txt>>



**KubeConfig:-**





<<Copy KubeConfig to Clipboard.txt>>





**Rancher Kubernetes Cluster config:-**



<<cluster01.txt>>









![](Aspose.Words.6d1da65b-4d1c-4460-859c-120cd6b26b9c.028.png)







![](Aspose.Words.6d1da65b-4d1c-4460-859c-120cd6b26b9c.029.png)







![](Aspose.Words.6d1da65b-4d1c-4460-859c-120cd6b26b9c.030.png)





![](Aspose.Words.6d1da65b-4d1c-4460-859c-120cd6b26b9c.031.png)





![](Aspose.Words.6d1da65b-4d1c-4460-859c-120cd6b26b9c.032.png)





![](Aspose.Words.6d1da65b-4d1c-4460-859c-120cd6b26b9c.033.png)



![](Aspose.Words.6d1da65b-4d1c-4460-859c-120cd6b26b9c.034.png)





Downloaded File

<<helm-operation-l76q6\_undefined.log>>









![](Aspose.Words.6d1da65b-4d1c-4460-859c-120cd6b26b9c.035.png)



![](Aspose.Words.6d1da65b-4d1c-4460-859c-120cd6b26b9c.036.png)



![](Aspose.Words.6d1da65b-4d1c-4460-859c-120cd6b26b9c.037.png)





![](Aspose.Words.6d1da65b-4d1c-4460-859c-120cd6b26b9c.038.png)



![](Aspose.Words.6d1da65b-4d1c-4460-859c-120cd6b26b9c.039.png)





![](Aspose.Words.6d1da65b-4d1c-4460-859c-120cd6b26b9c.040.png)



![](Aspose.Words.6d1da65b-4d1c-4460-859c-120cd6b26b9c.041.png)



![](Aspose.Words.6d1da65b-4d1c-4460-859c-120cd6b26b9c.042.png)



![](Aspose.Words.6d1da65b-4d1c-4460-859c-120cd6b26b9c.043.png)





![](Aspose.Words.6d1da65b-4d1c-4460-859c-120cd6b26b9c.044.png)



![](Aspose.Words.6d1da65b-4d1c-4460-859c-120cd6b26b9c.045.png)



![](Aspose.Words.6d1da65b-4d1c-4460-859c-120cd6b26b9c.046.png)







![](Aspose.Words.6d1da65b-4d1c-4460-859c-120cd6b26b9c.047.png)



![](Aspose.Words.6d1da65b-4d1c-4460-859c-120cd6b26b9c.048.png)



![](Aspose.Words.6d1da65b-4d1c-4460-859c-120cd6b26b9c.049.png)









![](Aspose.Words.6d1da65b-4d1c-4460-859c-120cd6b26b9c.050.png)





![](Aspose.Words.6d1da65b-4d1c-4460-859c-120cd6b26b9c.051.png)



![](Aspose.Words.6d1da65b-4d1c-4460-859c-120cd6b26b9c.052.png)



![](Aspose.Words.6d1da65b-4d1c-4460-859c-120cd6b26b9c.053.png)







![](Aspose.Words.6d1da65b-4d1c-4460-859c-120cd6b26b9c.054.png)





![](Aspose.Words.6d1da65b-4d1c-4460-859c-120cd6b26b9c.055.png)





![](Aspose.Words.6d1da65b-4d1c-4460-859c-120cd6b26b9c.056.png)







![](Aspose.Words.6d1da65b-4d1c-4460-859c-120cd6b26b9c.057.png)



![](Aspose.Words.6d1da65b-4d1c-4460-859c-120cd6b26b9c.058.png)



![](Aspose.Words.6d1da65b-4d1c-4460-859c-120cd6b26b9c.059.png)





![](Aspose.Words.6d1da65b-4d1c-4460-859c-120cd6b26b9c.060.png)





Downloaded file 



<<helm-operation-clprm\_undefined.log>>





![](Aspose.Words.6d1da65b-4d1c-4460-859c-120cd6b26b9c.061.png)


