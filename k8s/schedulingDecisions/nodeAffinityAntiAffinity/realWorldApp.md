
## ### [Real-World Application]

```
apiVersion: apps/v1
kind: Deployment
metadata:
  name: example-deployment
spec:
  replicas: 3
  template:
    metadata:
      labels:
        app: my-app
    spec:
      affinity:
        nodeAffinity:
          requiredDuringSchedulingIgnoredDuringExecution:
            nodeSelectorTerms:
            - matchExpressions:
              - key: disktype
                operator: In
                values:
                - ssd
        podAntiAffinity:
          requiredDuringSchedulingIgnoredDuringExecution:
            labelSelector:
              matchExpressions:
              - key: app
                operator: In
                values:
                - my-app
            topologyKey: "kubernetes.io/hostname"
      containers:
      - name: my-app-container
        image: my-app-image
```

This deployment ensures that the pods are only scheduled on nodes with SSDs and no two pods are placed on the same node, maximizing performance and fault tolerance.