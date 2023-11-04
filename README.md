# jenkins-master-slave
jenkins master slave architecture using k8s and helm


## Installation:
Run following command:


```
helm install jenkins-cicd .  
```

## Post Installation:
Run following command:

Windows:
```
set  POD_NAME=$(kubectl get pods --namespace default -l "app.kubernetes.io/name=jenkins-msarch,app.kubernetes.io/instance=jenkins-cicd" -o jsonpath="{.items[0].metadata.name}")
```
Linux based OS:
```
EXPORT  POD_NAME=$(kubectl get pods --namespace default -l "app.kubernetes.io/name=jenkins-msarch,app.kubernetes.io/instance=jenkins-cicd" -o jsonpath="{.items[0].metadata.name}")
```
Run Following command:

Windows:
```
set CONTAINER_PORT=$(kubectl get pod --namespace default $POD_NAME -o jsonpath="{.spec.containers[0].ports[0].containerPort}")
```
Linux based OS:
```
EXPORT CONTAINER_PORT=$(kubectl get pod --namespace default $POD_NAME -o jsonpath="{.spec.containers[0].ports[0].containerPort}")
```

Get the pods by running following command:

```
kubectl get pods
```
Then type following command for each of the pods replacing `POD_ID` and `HOST_PORT` for each of the 3 pods:

```
kubectl --namespace default port-forward POD_ID HOST_PORT:8080
```

example usage:

```
kubectl --namespace default port-forward jenkins-cicd-jenkins-msarch-6cd98fbdf4-hffmd 8082:8080
```
