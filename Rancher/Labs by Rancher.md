##
## Labs by Rancher
##


 

In-depth online workshop designed to give DevOps and IT teams the hands-on skills they need to deploy and manage Kubernetes everywhere.


Rancher Rodeo XIV - 2.7

 

 

![Picture1](https://github.com/ashrafkgit/Rancher/assets/134578702/acb3a451-c536-4332-a132-40b1e34c878e)

 

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

 

 

![image](https://github.com/ashrafkgit/Rancher/assets/134578702/626f4738-3840-4934-90b1-c8213bdd6540)

 

 

 

![image](https://github.com/ashrafkgit/Rancher/assets/134578702/a7323427-1c70-4a0d-a606-87954f4fd205)
![image](https://github.com/ashrafkgit/Rancher/assets/134578702/bb8832b9-56e1-4dc1-9b48-95965c09c734)


 

 

 

 

 

![image](https://github.com/ashrafkgit/Rancher/assets/134578702/a10f1d48-7cc3-4ecf-9031-12aec39353ea)

 

 

![image](https://github.com/ashrafkgit/Rancher/assets/134578702/024882fb-fc4d-43a8-aa96-2a6bc487dfac)

 

![image](https://github.com/ashrafkgit/Rancher/assets/134578702/dc0d7e6e-52d5-4c25-a54b-a8190b67e1e3)

 

 

 

 

 

 

![image](https://github.com/ashrafkgit/Rancher/assets/134578702/4bb50b91-96a4-4cc7-bf99-bbbdc3fb59a6)

 

 

 

 

## Rancher Kubernetes Cluster Bootstrapping

 

_Command syntax_
``` bash 
ec2-user@ip-172-31-44-121:~&gt; curl -fL <https://rancher.34.242.237.239.sslip.io/system-agent-install.sh> | sudo sh -s - --server <https://rancher.34.242.237.239.sslip.io> --label 'cattle.io/os=linux' --token cf55b9n5bcwtd4zzqgsdgfsz7xv78246gzzsrm9nqz5nq6frg4wrsf --ca-checksum e5b2f4cc07660772707d3c35a83e6f7c180f5a97301aa9e63282ac2e7b545262 --etcd --controlplane --worker --node-name cluster01
```

 


![image](https://github.com/ashrafkgit/Rancher/assets/134578702/99958cdf-f8e5-4461-af30-fd6604da22a2)

 

 

![image](https://github.com/ashrafkgit/Rancher/assets/134578702/802ced67-3377-42f6-8615-2b12c4336d38)

 

 

![image](https://github.com/ashrafkgit/Rancher/assets/134578702/5ac9f3f7-49ac-4927-a810-5745e7c86d38)

 

 

 

_Downloaded KUBE CONFIG File_

<<cluster01.yaml>>

 



 

 

 

 

![image](https://github.com/ashrafkgit/Rancher/assets/134578702/67b94efe-f7a8-4a2d-acb8-617bc301e5a9)

 

 

<<cluster01.yaml>>

 

 

**Rancher Management Server config:-**

> <<rancher01.txt>>

 

**KubeConfig:-**

> <<Copy KubeConfig to Clipboard.txt>> 

 

 **Rancher Kubernetes Cluster config:-**

 > <<cluster01.txt>>

 

 

 

 

![image](https://github.com/ashrafkgit/Rancher/assets/134578702/465c660b-cf78-4e6c-9279-95fb5bef02a6)

 

 

 

![image](https://github.com/ashrafkgit/Rancher/assets/134578702/9f117d28-8d64-420c-8cb4-2cb0fa44ae54)

 

 

 

![image](https://github.com/ashrafkgit/Rancher/assets/134578702/b5b3b2a8-4369-404f-9beb-cd045e2634b2)

 

 

![image](https://github.com/ashrafkgit/Rancher/assets/134578702/44f1c3dc-886d-4fea-998d-8a0532dd25e3)

 

 

![image](https://github.com/ashrafkgit/Rancher/assets/134578702/2a454e9b-a346-4e1c-bc98-5af6e861f806)

 

 

![image](https://github.com/ashrafkgit/Rancher/assets/134578702/8b037816-ed8d-40f8-b258-d2f1c17977fe)

 

![image](https://github.com/ashrafkgit/Rancher/assets/134578702/4469fcd7-cf72-4a57-9337-132d65222419)

 

 

_Downloaded File_

> <<helm-operation-l76q6_undefined.log>>

 

 

 

 

![image](https://github.com/ashrafkgit/Rancher/assets/134578702/dba69a7a-105e-4fdd-9cdb-af1ecfac386b)

 

![image](https://github.com/ashrafkgit/Rancher/assets/134578702/a0b391b2-02fb-41ca-896f-b0b3ce93ec5b)

 

![image](https://github.com/ashrafkgit/Rancher/assets/134578702/6772f95a-c8bb-402d-8967-454f06ae6211)

 

 

![image](https://github.com/ashrafkgit/Rancher/assets/134578702/9b191061-ed23-4eb5-ac02-e644af04c2d2)
![image](https://github.com/ashrafkgit/Rancher/assets/134578702/d6358757-09eb-412d-b5f8-c2bb46563bbf)


 

 

![image](https://github.com/ashrafkgit/Rancher/assets/134578702/07b94f73-a26a-4966-a296-210fe1242246)
![image](https://github.com/ashrafkgit/Rancher/assets/134578702/f2733ab3-bff2-4db5-aff3-d660030117fb)
![image](https://github.com/ashrafkgit/Rancher/assets/134578702/6621c428-2375-4505-8a3b-4124cbbf7d78)
![image](https://github.com/ashrafkgit/Rancher/assets/134578702/dc9bff2d-fbd4-40bc-a8e8-3a5e32ce3205)


 

 

![image](https://github.com/ashrafkgit/Rancher/assets/134578702/f56d4097-051e-407e-97f8-e0be6298a3f9)

 

![image](https://github.com/ashrafkgit/Rancher/assets/134578702/b09e4129-725e-45e0-a70c-53c9380da838)

 

![image](https://github.com/ashrafkgit/Rancher/assets/134578702/48961202-aba6-47a2-a532-4fc8b1fa50c7)

 

 

 

![image](https://github.com/ashrafkgit/Rancher/assets/134578702/ca2fdb08-dc9d-431f-b9d7-c9854d0febc6)

 

![image](https://github.com/ashrafkgit/Rancher/assets/134578702/5f8a6645-69ab-480e-ada6-35fa86f3cd5f)

 

![image](https://github.com/ashrafkgit/Rancher/assets/134578702/a9930db4-2300-4cf0-879a-80739281172d)

 

 

 

 

![image](https://github.com/ashrafkgit/Rancher/assets/134578702/87901fe7-da5e-4b92-b848-ed65577aa48f)

 

 

![image](https://github.com/ashrafkgit/Rancher/assets/134578702/c9949edb-0925-446c-abab-ee5762a294c2)

 

![image](https://github.com/ashrafkgit/Rancher/assets/134578702/27b8632e-8fb7-44b0-ab2c-069b09b2c926)

 

![image](https://github.com/ashrafkgit/Rancher/assets/134578702/e7fd2cef-7d41-4a1c-b5a0-b92d058858d5)

 

 

 

![image](https://github.com/ashrafkgit/Rancher/assets/134578702/33e7bd6b-7c95-49dc-b379-a9b5a809ca40)

 

 

![image](https://github.com/ashrafkgit/Rancher/assets/134578702/a07a626e-5341-48fd-8ec9-95cc1be05804)

 

 

![image](https://github.com/ashrafkgit/Rancher/assets/134578702/1ee5b51b-3ef3-42bb-a724-dd6d18e6b91d)

 

 

 

![image](https://github.com/ashrafkgit/Rancher/assets/134578702/d80c5d5d-6edf-46d8-80c6-a7e477ff3add)

 

![image](https://github.com/ashrafkgit/Rancher/assets/134578702/9b7fee27-3171-4155-b2cc-847f89e8eddb)

 

![image](https://github.com/ashrafkgit/Rancher/assets/134578702/6a5b07b7-2906-45cb-a162-4dad09e7c5f5)

 

 


_Downloaded file_

>  <<helm-operation-clprm_undefined.log>>

 

 

![image](https://github.com/ashrafkgit/Rancher/assets/134578702/1268314b-fc93-477c-b68f-125fe2e9a4ec)

 
