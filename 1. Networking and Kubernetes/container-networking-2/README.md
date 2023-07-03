# Network Modes in Linux Kernel
```
sudo docker network ls
```
| Network Mode     | Description                                                                                      |
|------------------|--------------------------------------------------------------------------------------------------|
| None             | No networking. Disables networking for the container. Use this mode when the container does not need network access. |
| Bridge           | The container runs in a private network internal to the host. Communication with other containers in the network is open. Communication with services outside the host goes through NAT before exiting the host. Bridge mode is the default mode of networking when the --net option is not specified. |
| Host             | The container shares the same IP address and network namespace as the host. Processes running inside this container have the same network capabilities as services running directly on the host. This mode is useful if the container needs access to network resources on the host. The container loses the benefit of network segmentation with this mode of networking. |
| Macvlan          | Macvlan uses a parent interface to create multiple subinterfaces with different MAC and IP addresses. Macvlan networks are segmented from each other, providing access within a network, but not between networks. Macvlan has four types: Private, VEPA, Bridge (default), and Passthrough. |
| IPvlan           | IPvlan is similar to Macvlan but does not assign MAC addresses to subinterfaces. All subinterfaces share the parent's MAC address but use different IP addresses. IPvlan has two modes: L2 (layer 2) and L3 (layer 3). |
| Overlay          | Allows for the extension of the same network across hosts in a container cluster. The overlay network sits on top of the physical networks. |
| Custom           | Similar to bridge networking but uses a bridge explicitly created for the container. Enables communication with multiple networks. |

# Docker Network Flow

![image](https://github.com/Pruthvi360/kubernetes-course/assets/107435692/c1bc5b8a-d6f0-4e9d-a1d2-1b312f5f1236)

# Overlay Networking (vxlan tunnel)

![image](https://github.com/Pruthvi360/kubernetes-course/assets/107435692/4b9ee684-f52f-4134-9eb7-5c66ae7ab23a)

# VXLAN TUNNEL with 16 million extension capability

![image](https://github.com/Pruthvi360/kubernetes-course/assets/107435692/299a6eb7-6f6b-41de-837a-907013bce3a8)

![image](https://github.com/Pruthvi360/kubernetes-course/assets/107435692/38eb23f4-717e-4bed-8546-6c235ce890b3)

# CNI plugins with various features and functionality.

| CNI                | Description                                                                                                                                                                                                                                                              |
|--------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Cilium             | Cilium is an open-source software for securing network connectivity between application containers. It is an L7/HTTP-aware CNI that enforces network policies on L3-L7 using an identity-based security model. Cilium utilizes eBPF, a Linux technology, to power its functionalities. |
| Flannel            | Flannel is a layer 3 network fabric designed for Kubernetes. It provides a simple way to configure networking in a Kubernetes cluster. Flannel uses the existing etcd datastore of the cluster to store its state information, eliminating the need for a dedicated datastore.          |
| Calico             | Calico combines flexible networking capabilities with run-anywhere security enforcement. It offers native Linux kernel performance and true cloud-native scalability. Calico configures a layer 3 network using the BGP routing protocol and provides full network policy support. It can integrate with Istio for policy enforcement at both service mesh and network infrastructure layers. |
| AWS VPC CNI        | AWS VPC CNI is an open-source implementation of a CNI specifically designed for Kubernetes on AWS. It leverages the native AWS network infrastructure and services, providing high throughput, low latency, and the ability to apply AWS VPC networking and security best practices.              |
