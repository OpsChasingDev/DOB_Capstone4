# DOB_Capstone4
Deploying a microservices application in Kubernetes with production and security best practices.

### Deploying the online shop microservices application

1. Create a managed K8s cluster in Linode (or other provider)
2. Download the kubeconfig.yaml file for the cluster
3. Set local env var "KUBECONFIG" to the path of the kubeconfig.yaml file
4. Navigate to the directory where the config.yaml file is held
5. Run the below command with kubectl to create a namespace for the application
   ```
   kubectl.exe create ns online-shop
   ```
6. Run the below command with kubectl to deploy the applicaiton to the K8s cluster
   ```
   kubectl.exe apply -f .\config.yaml -n online-shop
   ```

### Known Issues

There is an unresolved issue with the versioning/compatibility of the adservice microservice image, but it does not prevent the rest of the microservices application or the cluster from running and being stable.  See [this thread](https://techworld-with-nana.slack.com/archives/C01HFB3UHGX/p1678492219108779) in the DOB Slack for details.

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