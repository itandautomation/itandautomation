# Resource Limit

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: example-pod
spec:
  containers:
  - name: example-container
    image: nginx
    resources:
      limits:
        memory: "128Mi"
        cpu: "500m"
```