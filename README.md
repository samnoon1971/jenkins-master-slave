# Jenkins Master Slave Helm Chart
A Jenkins master slave-agent architecture using k8s and helm



## Badges

[![GPLv3 License](https://img.shields.io/badge/License-GPL%20v3-yellow.svg)](https://opensource.org/licenses/)
[![AGPL License](https://img.shields.io/badge/license-AGPL-blue.svg)](http://www.gnu.org/licenses/agpl-3.0)



## Authors

- [@samnoon1971](https://www.github.com/samnoon1971)


## Installation:
Run following command:


```
helm install jenkins-cicd .  
```

## Post Installation:
1. Run following command:

**Windows:**
```
set POD_NAME=$(kubectl get pods --namespace default -l "app.kubernetes.io/name=jenkins-msarch,app.kubernetes.io/instance=jenkins-cicd" -o jsonpath="{.items[0].metadata.name}")
```
**Linux based OS:**
```
EXPORT POD_NAME=$(kubectl get pods --namespace default -l "app.kubernetes.io/name=jenkins-msarch,app.kubernetes.io/instance=jenkins-cicd" -o jsonpath="{.items[0].metadata.name}")
```
2. Run Following command:

**Windows:**
```
set CONTAINER_PORT=$(kubectl get pod --namespace default $POD_NAME -o jsonpath="{.spec.containers[0].ports[0].containerPort}")
```
**Linux based OS:**
```
EXPORT CONTAINER_PORT=$(kubectl get pod --namespace default $POD_NAME -o jsonpath="{.spec.containers[0].ports[0].containerPort}")
```

3. To forward a local port to Jenkins GUI port (`8080`) on a Pod, get the pods by running following command:

```
kubectl get pods -l app.kubernetes.io/name=jenkins-msarch
```
Then type following command replacing `POD_ID` and `HOST_PORT` for any of the pods:

```
kubectl --namespace default port-forward POD_ID HOST_PORT:8080
```

***example usage:***

```
kubectl --namespace default port-forward jenkins-cicd-jenkins-msarch-6cd98fbdf4-hffmd 8082:8080
```

4. Update hosts file by browsing to `C:\Windows\System32\drivers\etc\hosts` for Windows and `/etc/hosts` for Linux systems, and add following lines to hosts file:

```
127.0.0.1 jenkins.master.local
127.0.0.1 jenkins.slave1.local
127.0.0.1 jenkins.slave2.local
```
***Note:*** You must replace `127.0.0.1` with the host IP of your environment.

## Support

For support, email samnoonabrar@gmail.com


## Feedback

If you have any feedback, please reach out to us at samnoonabrar@gmail.com
  
