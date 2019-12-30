# Find veth interface of docker containers

This repository contains a script for finding the veth interfaces of every
container. For example you might see a lot of veth interfaces on a K8s node/
docker host, but you can't figure out which namespace or container the veth
interface is associated with. This info can be helpful while debugging.
The script `docker-veth.sh` can be run from a privileged container on the same
node.

### Usage on K8s
Run a privileged pod using the samos123/docker-toolbox image that already
contains this script and other useful troubleshooting tools.

```
kubectl apply -f debug-pod.yaml
kubectl exec debug-pod -t -i bash
docker-veth.sh
```
