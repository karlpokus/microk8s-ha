# microk8s-ha
Trying out the new microk8s ha feature

> There are three components necessary for a highly available Kubernetes cluster:
1. There must be more than one node available at any time.
2. The control plane must be running on more than one node so that losing a single node would not render the cluster in-operable.
3. The cluster state must be in a datastore that is itself highly available

> All nodes of the HA cluster run the master control plane/.../A subset of the cluster nodes (at least three) maintain a copy of the Kubernetes dqlite database

# install

```bash
# on all nodes
$ snap install microk8s --classic
# on the first node
$ microk8s add-node
...
# on the other nodes
$ microk8s join <ip>:<port>/<token>
# repeat generating token and join all nodes
```

# todos
- [x] ha
- [ ] add k8s probes before node termination test
- [ ] ha-test: destroy node-03, run node-04 and join cluster, expect node-04 to also become master
- [ ] image registry (microk8s ctr images ls, ctr image import myimage.tar)
- [ ] node graceful exit (leave and remove-node <node> [--force])
