Example deploying the AWS LB Controller from the eks-charts helm repo.
  * https://github.com/aws/eks-charts/tree/master/stable/aws-load-balancer-controller

Run the following with a kubeconfig for the Rancher local cluster:

```yaml
cat <<EOF | kubectl apply -f -
kind: GitRepo
apiVersion: fleet.cattle.io/v1alpha1
metadata:
  name: aws-lb-controller
  namespace: fleet-default
spec:
  branch: main
  paths:
  - aws-lb-controller
  repo: https://github.com/dkeightley/fleet-testing
  targets:
  - clusterSelector:
      matchLabels:
        provider: aws
EOF
```

Now label any clusters with `provider: aws` where the controller should be deployed