## DOCKER

![image](https://github.com/Pruthvi360/kubernetes-course/assets/107435692/be1dc542-2353-4858-9d0b-c4a8fd3474cc)

## CRI-O

![image](https://github.com/Pruthvi360/kubernetes-course/assets/107435692/5e362e68-68bf-4ca2-a802-ae073fb73db6)

## Namespaces are features of the Linux kernel that isolate and virtualize system resources of a collection of processes.
## Here are examples of virtualized resources

| Namespace        | Description                                                                                     |
|------------------|-------------------------------------------------------------------------------------------------|
| PID namespace    | Processes ID, for process isolation.                                                            |
| Network namespace   | Manages network interfaces and a separate networking stack.                                      |
| IPC namespace    | Manages access to interprocess communication (IPC) resources.                                    |
| Mount namespace  | Manages filesystem mount points.                                                                |
| UTS namespace    | UNIX time-sharing; allows single hosts to have different host and domain names for different processes. |
| UID namespaces   | User ID; isolates process ownership with separate user and group assignments.                    |

# Inside Pod Network Architecture

![image](https://github.com/Pruthvi360/kubernetes-course/assets/107435692/5cd5b7c4-c299-47b1-9bc3-39f381196865)

# Steps to create the networking setup 

1. Create a host with a root network namespace.
2. Create a new network namespace.
3. Create a veth pair.
4. Move one side of the veth pair into a new network namespace.
5. Address side of the veth pair inside the new network namespace.
6. Create a bridge interface.
7. Address the bridge interface.
8. Attach the bridge to the host interface.
9. Attach one side of the veth pair to the bridge interface.
10. Profit.

# List of commands

```
$ echo 1 > /proc/sys/net/ipv4/ip_forward
$ sudo ip netns add net1
$ sudo ip link add veth0 type veth peer name veth1
$ sudo ip link set veth1 netns net1
$ sudo ip link add veth0 type veth peer name veth1
$ sudo ip netns exec net1 ip addr add 192.168.1.101/24 dev veth1
$ sudo ip netns exec net1 ip link set dev veth1 up
$ sudo ip link add br0 type bridge
$ sudo ip link set dev br0 up
$ sudo ip link set enp0s3 master br0
$ sudo ip link set veth0 master br0
$ sudo ip netns exec net1  ip route add default via 192.168.1.100
```

## Create Network Namespaces in Ubuntu 
```
sysctl net.ipv4.ip_forward
sudo echo 1 > /proc/sys/net/ipv4/ip_forward
sysctl net.ipv4.ip_forward
sudo ip netns list
sudo ip netns add net1
sudo ip netns list net1
```
## ip again allows administrators to create the veth pairs with a straightforward command
```
sudo ip link add veth0 type veth peer name veth1
```
## Now let’s move veth1 into the new network namespace created previously:
```
vagrant@ubuntu-xenial:~$ sudo ip link set veth1 netns net1
```
## ip netns exec allows us to verify the network namespace’s configuration.
## The output verifies that veth1 is now in the network namespace net:
```
sudo ip netns exec net1 ip link list
```
## As with host networking interfaces, they will need to be “turned on”:
```
sudo ip netns exec net1 ip link set dev veth1 up
```
## The state has now transitioned to LOWERLAYERDOWN. 
The status NO-CARRIER points in the right direction. 
Ethernet needs a cable to be connected; our upstream veth pair is not on yet either. 
The veth1 interface is up and addressed but effectively still “unplugged”:
```
sudo ip netns exec net1 ip link list veth1
```
## Let’s turn up the veth0 side of the pair now:
```
sudo ip link set dev veth0 up
sudo ip link list
```

## Both sides of the veth pair report up; we need to connect the root namespace veth side to the bridge interface.
Make sure to select the interface you’re working with, in this case enp0s8;
it may be different for others:
```
sudo ip link add br0 type bridge
sudo ip link set dev br0 up
sudo ip link set enp0s8 master br0
sudo ip link set veth0 master br0
```

## We can see that the enp0s8 and veth0 report are part of the bridge br0 interface, master br0 state up.
```
ing 192.168.1.100 -c 4
PING 192.168.1.100 (192.168.1.100) 56(84) bytes of data.
From 192.168.1.10 icmp_seq=1 Destination Host Unreachable
```
## Our new network namespace does not have a default route, so it does not know where to route our packets for the ping requests:
```
sudo ip netns exec net1
```
## Let’s try that again:
```
$ ping 192.168.2.100 -c 4
PING 192.168.2.100 (192.168.2.100) 56(84) bytes of data.
64 bytes from 192.168.2.100: icmp_seq=1 ttl=64 time=0.018 ms
```

# RECAP
```
$ echo 1 > /proc/sys/net/ipv4/ip_forward
$ sudo ip netns add net1
$ sudo ip link add veth0 type veth peer name veth1
$ sudo ip link set veth1 netns net1
$ sudo ip link add veth0 type veth peer name veth1
$ sudo ip netns exec net1 ip addr add 192.168.1.101/24 dev veth1
$ sudo ip netns exec net1 ip link set dev veth1 up
$ sudo ip link add br0 type bridge
$ sudo ip link set dev br0 up
$ sudo ip link set enp0s3 master br0
$ sudo ip link set veth0 master br0
$ sudo ip netns exec net1  ip route add default via 192.168.1.100
```
