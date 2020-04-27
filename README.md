# CKAD Prep


## Day 4
 
### Ambassdor PatternForwarding Port Traffic with an Ambassador Container
- We will have one pod which is running at one pod and will be directing the traffic to hardcoded another port of different pod
- Basically one pod having two containers.. one container exposing port 80 the same container then using config map to get the urls and other parameters and call the second container at a different port.  So this is more likely an ambassdor pattern.

## Day 5

### Container logging and metrix
```
kubectl logs <pod name> gives the detailed log
```

- An option to add container name is der with -c as one pod can have multiple containers runningin normally
- Metrix server is more to monitor the health you can us
```
kubectl get top pods
kubectl get top pod <pod name>
kubectl get top nodes
```  

## Day 6

### Container debugging
- Basically when a container fails to start the different ways to know and find the root cause 

```
kubectl log
kubectl describe 
kubectl get pod <podname> -o yaml --export > <filename>
```
- Implement readiness and liveness probe also to find root cause

## Day 7

### Lables, annotations selector, Deployment, rolling update and Cronjobs

- Lables is like rather than regfering pods by names etc you can apply filter select via lables. where as annotation is like metadata
```yaml
kubectl describe pod my-production-label-pod
kubectl get pods -l app=my-app

kubectl get pods -l environment=production

kubectl get pods -l environment=development

kubectl get pods -l environment!=production

kubectl get pods -l 'environment in (development,production)'

kubectl get pods -l app=my-app,environment=production
kubectl describe pod my-annotation-pod
```

- Deployment is like you define how many pods should be running at time.Deployments provide a variety of features to help you automatically manage groups of replica pods.

```yaml
kubectl get deployments

kubectl get deployment <deployment name>

kubectl describe deployment <deployment name>

kubectl edit deployment <deployment name>

kubectl delete deployment <deployment name>
```
- Rolling updates when u need to upgrade things or rollback to move any step becoz of issue

```yaml
kubectl set image deployment/rolling-deployment nginx=nginx:1.7.9 --record
kubectl rollout history deployment/rolling-deployment

kubectl rollout history deployment/rolling-deployment --revision=2
kubectl rollout undo deployment/rolling-deployment
kubectl rollout undo deployment/rolling-deployment --to-revision=1
```
- Jobs and cron jobs - job run for once and cron as always scheudled

```
kubectl get jobs
kubectl get cronjobs
```
## Day 8

### Services and network policies

- Services are used for providing network access to pods and components whether with in pod to pod via clusterip or to outside world by Nodeport
```cmd
kubectl get svc
kubectl get endpoints my-service
````

## Day 9

### Network policies

- network policy can be allowed at pod, namespace or ip level.  
- the network policy apply to all matching combinations of selector specified such as pod, ns or ip level.

```
kubectl get networkpolicies
kubectl describe networkpolicy my-network-policy
```

### Volume PV PVC

- volume is for storage volume mount to emptydir is like till the node remains. and same volume can be mounted to multiple pods
- Persistant data store persistent volume nd pvc