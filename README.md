# CKAD Prep


## Day 4
 
### Ambassdor PatternForwarding Port Traffic with an Ambassador Container
- We will have one pod which is running at one pod and will be directing the traffic to hardcoded another port of different pod
- Basically one pod having two containers.. one container exposing port 80 the same container then using config map to get the urls and other parameters and call the second container at a different port.  So this is more likely an ambassdor pattern.

