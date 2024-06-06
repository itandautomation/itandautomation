# Resource Quotas and Limit Ranges

```yaml
apiVersion: v1
kind: ResourceQuota
metadata:
  name: example-quota
  namespace: example-namespace
spec:
  hard:
    requests.cpu: "1"
    requests.memory: "1Gi"
    limits.cpu: "2"
    limits.memory: "2Gi"

```


This resource quota ensures that all pods in the `example-namespace` collectively don’t exceed 1 CPU and 1 GiB of memory in requests, and 2 CPUs and 2 GiB of memory in limits.


```yaml
apiVersion: v1
kind: LimitRange
metadata:
  name: example-limitrange
  namespace: example-namespace
spec:
  limits:
  - default:
      cpu: "500m"
      memory: "128Mi"
    defaultRequest:
      cpu: "250m"
      memory: "64Mi"
    type: Container

```