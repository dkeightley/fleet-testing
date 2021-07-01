Example deloying rancher-monitoring via fleet

```yaml
kind: GitRepo
apiVersion: fleet.cattle.io/v1alpha1
metadata:
  name: monitoring
  namespace: fleet-default
spec:
  branch: monitoring
  paths:
  - monitoring-crd
  - monitoring
  paused: false
  repo: https://github.com/dkeightley/fleet-testing
```