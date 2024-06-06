# Managing Resource Overcommitment

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: overcommitted-pod
spec:
  containers:
  - name: example-container
    image: nginx
    resources:
      requests:
        memory: "32Mi"
        cpu: "100m"
      limits:
        memory: "256Mi"
        cpu: "1"
```