# Linux Networking

## The Bridge Interface
 The bridge interface allows system administrators to create multiple layer 2 networks on a single host.
 The bridge functions like a network switch between network interfaces on a host
![image](https://github.com/Pruthvi360/kubernetes-course/assets/107435692/92852589-1bd6-45a0-ae70-29299b6af116)


# Creating bridge interface and connecting veth pair
# # Add a new bridge interface named br0.
```
ip link add br0 type bridge
```
# # Attach eth0 to our bridge.
```
ip link set eth0 master br0
```
# # Attach veth to our bridge.
```
ip link set veth master br0
```
## brctl commands

| Command        | Description                                            |
|----------------|--------------------------------------------------------|
| addbr          | Add a bridge                                           |
| delbr          | Delete a bridge                                        |
| addif          | Add an interface to a bridge                            |
| delif          | Delete an interface from a bridge                       |
| setageing      | Set the ageing time for a bridge                        |
| setbridgeprio  | Set the priority of a bridge                            |
| setfd          | Set the forward delay for a bridge                      |
| sethello       | Set the hello time for a bridge                         |
| setmaxage      | Set the maximum message age for a bridge                |
| setpathcost    | Set the path cost for a specific port on a bridge       |
| setportprio    | Set the priority of a specific port on a bridge         |
| show           | Show a list of bridges                                  |
| showmacs       | Show a list of MAC addresses associated with a bridge    |
| showstp        | Show STP (Spanning Tree Protocol) information for a bridge |
| stp            | Turn on/off STP (Spanning Tree Protocol) for a bridge   |

## IP talbles

| Table    | Purpose                                                        |
|----------|----------------------------------------------------------------|
| Filter   | Handles acceptance and rejection of packets                     |
| NAT      | Modifies the source or destination IP addresses                |
| Mangle   | Performs general-purpose editing of packet headers              |
| Raw      | Allows packet mutation before connection tracking and other tables |
| Security | Used by SELinux for packet handling (applicable with SELinux)   |

## iptables chains and corresponding Netfilter hooks

| iptables Chain | Netfilter Hook       |
|----------------|----------------------|
| PREROUTING     | NF_IP_PRE_ROUTING    |
| INPUT          | NF_IP_LOCAL_IN       |
| NAT            | NF_IP_FORWARD        |
| OUTPUT         | NF_IP_LOCAL_OUT      |
| POSTROUTING    | NF_IP_POST_ROUTING   |

## iptables chains executed in various scenarios

| Packet Description                                                     | Packet Source | Packet Destination | Tables Processed                           |
|------------------------------------------------------------------------|---------------|--------------------|--------------------------------------------|
| An inbound packet, from another machine.                                | 10.0.0.2      | 10.0.0.1           | PREROUTING, INPUT                          |
| An inbound packet, not destined for this machine.                       | 10.0.0.2      | 10.0.0.3           | PREROUTING, NAT, POSTROUTING               |
| An outbound packet, originating locally, destined for another machine.  | 10.0.0.1      | 10.0.0.2           | OUTPUT, POSTROUTING                         |
| A packet from a local program, destined for the same machine.           | 127.0.0.1     | 127.0.0.1          | OUTPUT, POSTROUTING (loopback: PREROUTING, INPUT) |

## EXAMPLES
```
iptables -A OUTPUT -p tcp --dport 22 -j LOG --log-level info --log-prefix "ssh-output"
```

## Which iptables tables (rows) contain which chains (columns)

| iptables Chain  | Raw   | Mangle | NAT   | Filter |
|-----------------|-------|--------|-------|--------|
| PREROUTING      |   ✓   |   ✓    |   ✓   |        |
| INPUT           |   ✓   |   ✓    |   ✓   |        |
| FORWARD         |   ✓   |   ✓    |       |        |
| OUTPUT          |   ✓   |   ✓    |   ✓   |   ✓    |
| POSTROUTING     |   ✓   |   ✓    |   ✓   |        |

**NOTE** : iptables -L -t <table>

## Some common iptables match types

| Match Type    | Flag(s)                         | Description                                                     |
|---------------|---------------------------------|-----------------------------------------------------------------|
| Source        | -s, --src, --source             | Matches packets with the specified source address               |
| Destination   | -d, --dest, --destination       | Matches packets with the specified destination address          |
| Protocol      | -p, --protocol                  | Matches packets with the specified protocol                     |
| In Interface  | -i, --in-interface              | Matches packets that entered via the specified interface        |
| Out Interface | -o, --out-interface             | Matches packets that are leaving via the specified interface    |
| State         | -m state --state <states>       | Matches packets from connections that are in specified states    |

## LoadBalancing in Linux OR Kubernetes 
IPVS modes supported in Kubernetes
```
NAT rewrites source and destination addresses.
DR encapsulates IP datagrams within IP datagrams.
IP tunneling directly routes packets to the backend server by rewriting the MAC address of the data frame with the MAC address of the selected backend server.
```

## Cheat sheet of common debugging cases and tools

| Case                      | Tools                                                             |
|---------------------------|-------------------------------------------------------------------|
| Checking connectivity     | traceroute, ping, telnet, netcat                                  |
| Port scanning             | nmap                                                              |
| Checking DNS records      | dig, commands mentioned in "Checking Connectivity"                |
| Checking HTTP/1           | cURL, telnet, netcat                                              |
| Checking HTTPS            | OpenSSL, cURL                                                     |
| Checking listening programs | netstat                                                           |

## Useful traceroute options

| Option          | Syntax                | Description                                                                                                        |
|-----------------|-----------------------|--------------------------------------------------------------------------------------------------------------------|
| First TTL       | -f <TTL>, -M <TTL>    | Set the starting IP TTL (default value: 1). Setting the TTL to n will cause traceroute to not report the first n-1 hosts en route to the destination. |
| Max TTL         | -m <TTL>              | Set the maximum TTL, i.e., the maximum number of hosts that traceroute will attempt to route through.             |
| Protocol        | -P <protocol>         | Send packets of the specified protocol (TCP, UDP, ICMP, and sometimes other options). UDP is the default.         |
| Source address  | -s <address>          | Specify the source IP address of outgoing packets.                                                                 |
| Wait            | -w <seconds>          | Set the time to wait for a probe response.                                                                          |


## shows common dig options.

| Option        | Syntax               | Description                                                                                    |
|---------------|----------------------|------------------------------------------------------------------------------------------------|
| IPv4          | -4                   | Use IPv4 only.                                                                                 |
| IPv6          | -6                   | Use IPv6 only.                                                                                 |
| Address       | -b <address>[#<port>] | Specify the address to make a DNS query to. Port can optionally be included, preceded by #.    |
| Port          | -p <port>            | Specify the port to query, in case DNS is exposed on a nonstandard port. Default is 53.        |
| Domain        | -q <domain>          | The domain name to query.                                                                      |
| Record Type   | -t <type>            | The DNS record type to query.                                                                  |

## shows common netstat options.

| Option               | Syntax     | Description                                                                                                                   |
|----------------------|------------|-------------------------------------------------------------------------------------------------------------------------------|
| Show all sockets     | netstat -a | Shows all sockets, not only open connections.                                                                                 |
| Show statistics      | netstat -s | Shows networking statistics. By default, netstat shows stats from all protocols.                                              |
| Show listening sockets | netstat -l | Shows sockets that are listening. This is an easy way to find running services.                                                |
| TCP                  | netstat -t | The -t flag shows only TCP data. It can be used with other flags, e.g., -lt (show sockets listening with TCP).               |
| UDP                  | netstat -u | The -u flag shows only UDP data. It can be used with other flags, e.g., -lu (show sockets listening with UDP).               |

## netcat
```
netcat <address> <port>
```

## OpenSSL
```
openssl list --commands
openssl [sub-command] [arguments] [options]
openssl s_client -connect k8s.io:443
```
