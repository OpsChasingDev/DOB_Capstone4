# DOB_Capstone4
Deploying a microservices application in Kubernetes with production and security best practices.

### Deployment/Service Skeletons

```yaml
---
apiVersion: apps/v1
kind: Deployment
metadata:
  name: xxx
spec:
  selector:
    matchLabels:
      app: xxx
  template:
    metadata:
      labels:
        app: xxx
    spec:
      containers:
      - name: xxx
        image: xxx
        ports:
        - containerPort: xxx
---
apiVersion: v1
kind: Service
metadata:
  name: xxx
spec:
  type: ClusterIP
  selector:
    app: xxx
  ports:
  - protocol: TCP
    port: xxx
    targetPort: xxx
```