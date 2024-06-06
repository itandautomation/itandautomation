# Real-World Application

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: critical-service
spec:
  replicas: 3
  template:
    metadata:
      labels:
        app: critical
    spec:
      containers:
      - name: critical-container
        image: critical-service-image
        resources:
          requests:
            memory: "128Mi"
            cpu: "500m"
          limits:
            memory: "256Mi"
            cpu: "1"

---
apiVersion: apps/v1
kind: Deployment
metadata:
  name: non-critical-service
spec:
  replicas: 3
  template:
    metadata:
      labels:
        app: non-critical
    spec:
      containers:
      - name: non-critical-container
        image: non-critical-service-image
        resources:
          requests:
            memory: "64Mi"
            cpu: "250m"
          limits:
            memory: "128Mi"
            cpu: "500m"
```