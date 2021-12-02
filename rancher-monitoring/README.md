Example deloying rancher-monitoring via fleet.

Run the following with a kubeconfig for the Rancher local cluster:

```yaml
cat <<EOF | kubectl apply -f -
kind: GitRepo
apiVersion: fleet.cattle.io/v1alpha1
metadata:
  name: monitoring
  namespace: fleet-default
spec:
  branch: main
  paths:
  - rancher-monitoring/01-monitoring
  paused: false
  repo: https://github.com/dkeightley/fleet-testing
  targets:
  - clusterSelector:
      matchLabels:
        monitoring: enabled
EOF
```

Now label any clusters with `monitoring: enabled` where monitoring should be deployed