### multi tenacy

#### NODES
use constrants to stop running on certain nodes

#### Networks
creating different networks creates isolation.

### Kubernetes

#### NODES
creating pod tolerations and node taint will achive the same as constrants

#### networking
for doing network isolation, you need to setup network policies

## Observability

### Swarm
mgmt plane - cluster key-value store based on raft control plane: gossip based cluster
data plane
linux network namespaces iptables, IPVS

metrics through swarm events

### Kubernetes
kubectl grabs resources of the cluster to access things like etcd state store

data plane
linux l3 forwarding iptables and ipsets

metrics through prometheus
