
## Node Anti-Affinity prevents pods from being scheduled on certain nodes based on labels

```
apiVersion: v1
kind: Pod
metadata:
  name: example-pod
spec:
  affinity:
    podAntiAffinity:
      requiredDuringSchedulingIgnoredDuringExecution:
        labelSelector:
          matchExpressions:
          - key: app
            operator: In
            values:
            - front-end
        topologyKey: "kubernetes.io/hostname"
```

In this example, the pod will not be scheduled on a node that already has a pod with the label `app=front-end`. The `topologyKey` here is `kubernetes.io/hostname`, which means the anti-affinity rule is applied at the node level.