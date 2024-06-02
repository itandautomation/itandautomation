
## Preferred During Scheduling, Ignored During Execution

```
apiVersion: v1
kind: Pod
metadata:
  name: example-pod
spec:
  affinity:
    nodeAffinity:
      preferredDuringSchedulingIgnoredDuringExecution:
        preference:
          matchExpressions:
          - key: disktype
            operator: In
            values:
            - ssd

```

Here, the scheduler will prefer nodes with `disktype=ssd`, but if none are available, it will still schedule the pod on a different node.