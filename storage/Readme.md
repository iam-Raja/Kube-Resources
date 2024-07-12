## Deploy driver ##
**1.Create the volume in same node AZ**
* EBS in same region
* EFS anywhere

**2.EBS Drivers:Github-aws-ebs-csi-driver**

* You may deploy the EBS CSI driver via Kustomize

```
kubectl apply -k "github.com/kubernetes-sigs/aws-ebs-csi-driver/deploy/kubernetes/overlays/stable/?ref=release-1.32"
```

* Github for EBS-Vloume
```
aws-ebs-csi-driver
```

**EFS Drivers:Github-aws-efs-csi-driver**
* Download the manifest. Replace release-X.X with your desired branch. We recommend using the latest released version. For a list of active branches, see Branches.
* At present Latest relase is release-2.0
```
kubectl kustomize \
    "github.com/kubernetes-sigs/aws-efs-csi-driver/deploy/kubernetes/overlays/stable/?ref=release-2.0" > public-ecr-driver.yaml
```
* Apply the manifest
```
kubectl apply -f public-ecr-driver.yaml
```

**Finally Check is drivers installed**
```
kubectl get pods -n kube-system
```
**3.Attach Ebs policy to nodes-roles**
* EBS
```
AmazonEBSCSIDriverPolicy
```

*EFS
```
AmazonEFSCSIDriverPolicy
```

**4.To access App's created with EbS**

* Make sure LB-SG is opened on valid ports and instances opened on nodeport

**5.To access App's created with EFS**
* Allow Ec2-instance-SG on NFS protocol with EFS-SG
* While deleting cluster remove this manually added sg rule first and EFS Volume later delete cluster


![Screenshot 2024-07-12 114943](https://github.com/user-attachments/assets/799a5e0c-2a18-45ca-9063-9ca57fd22fe4)
