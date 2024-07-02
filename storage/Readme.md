## Deploy driver ##
* You may deploy the EBS CSI driver via Kustomize

```kubectl apply -k "github.com/kubernetes-sigs/aws-ebs-csi-driver/deploy/kubernetes/overlays/stable/?ref=release-1.32"
```