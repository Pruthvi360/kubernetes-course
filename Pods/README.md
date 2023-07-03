## Using init containers
```
A) init containers have separate images from app containers, they have some advantages for start-up related code

1. Init containers can contain utilities or custom code for setup that are not present in an app image
2. The application image builder and deployer roles can work independently without the need to jointly build a single app image.
3. Init containers can run with a different view of the filesystem than app containers in the same Pod. Consequently, they can be given access to Secrets that app containers cannot access.
4. Because init containers run to completion before any app containers start, init containers offer a mechanism to block or delay app container startup until a set of preconditions are met. Once preconditions are met, all of the app containers in a Pod can start in parallel.
5. Init containers can securely run utilities or custom code that would otherwise make an app container image less secure. By keeping unnecessary tools separate you can limit the attack surface of your app container image.
# Running 2 containers inside the pods
```
## Yaml file to create pods 
```
apiVersion: v1
kind: Pod
metadata:
  name: myapp-pod
  labels:
    app.kubernetes.io/name: MyApp
spec:
  containers:
  - name: myapp-container
    image: busybox:1.28
    command: ['sh', '-c', 'echo The app is running! && sleep 3600']
  initContainers:
  - name: init-myservice
    image: busybox:1.28
    command: ['sh', '-c', "until nslookup myservice.$(cat /var/run/secrets/kubernetes.io/serviceaccount/namespace).svc.cluster.local; do echo waiting for myservice; sleep 2; done"]
  - name: init-mydb
    image: busybox:1.28
    command: ['sh', '-c', "until nslookup mydb.$(cat /var/run/secrets/kubernetes.io/serviceaccount/namespace).svc.cluster.local; do echo waiting for mydb; sleep 2; done"]
```
# Run Command 
```
kubectl apply -f myapp.yaml
```
# Check the Status
```
kubectl get -f myapp.yaml
```
# See logs for the container inside the pods
```
kubectl logs myapp-pod -c init-myservice # Inspect the first init container
kubectl logs myapp-pod -c init-mydb      # Inspect the second init container
```
# Creating the service for 2 containers inside the pods
##  init containers will be waiting to discover Services named mydb and myservice
```
---
apiVersion: v1
kind: Service
metadata:
  name: myservice
spec:
  ports:
  - protocol: TCP
    port: 80
    targetPort: 9376
---
apiVersion: v1
kind: Service
metadata:
  name: mydb
spec:
  ports:
  - protocol: TCP
    port: 80
    targetPort: 9377
```
# To create the mydb and myservice services:
```
kubectl apply -f services.yaml
```
# You'll then see that those init containers complete, and that the myapp-pod Pod moves into the Running state:
```
kubectl get -f myapp.yaml
```
