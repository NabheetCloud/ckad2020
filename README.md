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