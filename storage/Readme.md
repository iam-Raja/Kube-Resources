## Deploy driver ##

**EBS Drivers:Github-aws-ebs-csi-driver**
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