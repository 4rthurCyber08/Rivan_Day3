
<!-- Your monitor number = #$34T# -->

## ⛅ Warm Up for Day 3.

<br>

### 🔧 Configure the following:
  - Switch (__CoreTAAS__ & __CoreBABA__)
  - Voice Gateway/Call Manager (__CUCM - Cisco Unified Call Manager__)
  - Router (__EDGE__)

<br>

| CIDR | SUBNET MASK     | RIVAN    | WILDCARD     |
| ---  | ---             | ---      | ---          |
| /18  |                 |          |              |
|      | 255.255.255.224 |          |              |
|      |                 | 2nd, 4i  |              |
|      |                 |          | 0.0.0.3      |

<br>

| BitLen |       |
| ---    | ---   |
| 42     |       |
| 1800   |       |
| 365    |       |
| 980    |       |
| 112    |       |

<br>

### Design a network for teleperformance.com with 720 users. Use the available IP address space 10.42.0.0 /16

> C:

<br> 

> S:

<br>

> I:  

<br>

| teleperformance.com     | IPv4  |
| ---                     | ---   |
| Network                 |       |
| First Valid             |       |
| Last Valid              |       |
| Last IP/Broadcast       |       |
| ---                     | ---   |
| NOT teleperformance.com |       |

&nbsp;
---
&nbsp;

### Configure 32 offices for teleperformance.com using the available network address 192.168.0.0/16. Determine the first & last valid IP of the 4th office

> C:

<br> 

> A:

<br>

> I:  

<br>

| teleperformance.com     | IPv4  |
| ---                     | ---   |
| 4th Office: Network     |       |
| First Valid             |       |
| Last Valid              |       |
| Last IP/Broadcast       |       |
| ---                     | ---   |
| NOT 4th Office          |       |

<br>
<br>

---
&nbsp;

## 🎯 Review

### 1. What is the reason for the error?

~~~
Router(config)# interface GigabitEthernet 1/0/1
Router(config-if)# ip add 192.168.16.143 255.255.255.240
Bad Mask /28 for address 192.168.16.143
~~~

&nbsp;
---
&nbsp;

### 2. Devices fail to obtain IP addresses from a DHCP server. Determine the issue by going through the dhcp configurations shown below.

~~~
Router# show run | s dhcp
ip dhcp excluded-address 10.28.0.1 10.28.0.100
ip dhcp pool mainpool
 network 10.28.0.0 255.255.255.248
 default-router 10.28.0.1 
 domain-name main.com
 dns-server 10.28.1.10
~~~

&nbsp;
---
&nbsp;

### 3. Match the Host addresses on the left to their correct IP range on the right.

|     | Host                |         ---        |     | Range (1st Valid - Broadcast)     |
| --- | ---                 | ---                | --- | ---                               |
| 1   | 10.187.45.21 /14    |                    | A   | 192.168.100.193 - 192.168.100.223 |
| 2   | 10.180.201.90 /12   |                    | B   | 10.176.0.1 - 10.191.255.255       |
| 3   | 172.16.74.5 /20     |                    | C   | 172.16.64.1 - 172.16.79.255       |
| 4   | 172.16.81.1 /19     |                    | D   | 192.168.100.193 - 192.168.100.208 |
| 5   | 192.168.100.203 /27 |                    | E   | 10.184.0.1 - 10.187.255.255       |
| 6   | 192.168.100.195 /28 |                    | F   | 172.16.64.1 - 172.16.95.255       |

&nbsp;
---
&nbsp;

### 4. Design a network for Cognizant.com with 4720 potential users. Use the IP address space 10.42.0.0 /16

> C:

<br> 

> S:

<br>

> I:  

<br>

| Cognizant.com     | IPv4  |
| ---               | ---   |
| Network           |       |
| First Valid       |       |
| Last Valid        |       |
| Last IP/Broadcast |       |
| ---               | ---   |
| NOT Cognizant.com |       |


&nbsp;
---
&nbsp;

### 5. Which goal is achieved by the implementation of private IPv4 addressing on a network?
  - [ ] __A.__ provides an added level of protection against Internet exposure
  - [ ] __B.__ provides a reduction in size of the forwarding table on network routers
  - [ ] __C.__ allows communication across the Internet to other private networks
  - [ ] __D.__ allows servers and workstations to communicate across public network boundaries

&nbsp;
---
&nbsp;

### 6. Which two options are the best reasons to use an IPV4 private IP space? (Choose two.)
  - [ ] __A.__ to enable intra-enterprise communication
  - [ ] __B.__ to implement NAT
  - [ ] __C.__ to connect applications
  - [ ] __D.__ to conserve global address space
  - [ ] __E.__ to manage routing overhead

&nbsp;
---
&nbsp;

### 7. Which component of an Ethernet frame is used to notify a host that traffic is coming?
  - [ ] __A.__ Start of Frame Delimiter
  - [ ] __B.__ Type Field
  - [ ] __C.__ Preamble
  - [ ] __D.__ Data Field

&nbsp;
---
&nbsp;

### 8. Based on the diagram below, what command was entered on the device's Ethernet1/1 interface that registered the following entry to its routing table.
~~~
C        10.1.4.4/30 is directly connected, Ethernet1/1
L        10.1.4.6/32 is directly connected, Ethernet1/1
~~~
  - [ ] __A.__ `router(config-if)# ip address 10.1.4.4 255.255.255.252`
  - [ ] __B.__ `router(config-if)# ip address 10.1.4.4 255.255.255.255`
  - [ ] __C.__ `router(config-if)# ip address 10.1.4.6 255.255.255.252`
  - [ ] __D.__ `router(config-if)# ip address 10.1.4.6 255.255.255.255`

&nbsp;
---
&nbsp;

### 9. What is the destination MAC address of a broadcast frame?
  - [ ] __A.__ 00:00:0c:07:ac:01
  - [ ] __B.__ ff:ff:ff:ff:ff:ff
  - [ ] __C.__ 33:2e:08:00:00:0c
  - [ ] __D.__ 00:00:0c:43:2e:08
  - [ ] __E.__ 00:00:0c:ff:ff:ff

&nbsp;
---
&nbsp;

### 10. Based on the diagram, what is the subnet mask for VLAN 100?
~~~
Gateway of last resort is not set
      10.0.0.0/8 is variably subnetted, 6 subnets, 3 masks
C        10.1.4.4/30 is directly connected, Ethernet1/1
L        10.1.4.6/32 is directly connected, Ethernet1/1
C        10.2.1.0/24 is directly connected, Vlan10
L        10.2.1.1/32 is directly connected, Vlan10
C        10.2.2.0/24 is directly connected, Vlan20
L        10.2.2.1/32 is directly connected, Vlan20
      192.168.1.0/24 is variably subnetted, 2 subnets, 2 masks
C        192.168.1.128/27 is directly connected, Vlan100
L        192.168.1.129/32 is directly connected, Vlan100
      192.168.100.0/24 is variably subnetted, 2 subnets, 2 masks
C        192.168.100.192/29 is directly connected, Loopback1
L        192.168.100.195/32 is directly connected, Loopback1
~~~

  - [ ] __A.__ 255.255.255.0
  - [ ] __B.__ 255.255.255.252
  - [ ] __C.__ 255.255.255.224
  - [ ] __D.__ 255.255.255.255
  - [ ] __E.__ 255.255.255.248

<br>
<br>

---
&nbsp;

# 🏢 Establish Network Connectivity

Jobs of a router:  
1. &nbsp;
2. &nbsp;
3. &nbsp;
4. &nbsp;
5. &nbsp;

Static/Default Routing = Minimum Wage  
OSPF/EIGRP = 30k-40k  
BGP = 100k up  
VPN = 30-40k  

<br>

## Job Interview Questions for L1/L2 NOC-MSP postions.
### Interpret the components of a Routing Table.
A routing table is a database, also known as a FIB (Forwarding Information Base), used by network devices to determine the most efficient path for data packets as they travel across a network.
- Linux: `netstat -rn`
- Windows: `route print`
- Cisco: `show ip interface brief`

<br>
<br>

---
&nbsp;

## Master Routing using RIVAN RSTHAYUP LAB
~~~
Login: root
Pass: C1sc0123

Lab: RSTvX

Devices
Secret: pass
~~~

<br>

![RST_IPv4](img/rstIPv4.png)

&nbsp;
---
&nbsp;

### 🎯 Exercise 01: Review on DHCP & IP addressing.
What are the steps to configure DHCP?  
1. Exclude IP addresses
2. Create DHCP pool
    - Network
    - Default-Router
    - Domain-Name
    - DNS-Server

3. Assign DHCP clients

<br>

### DHCP Process
| Acronym | Full Form   | Traffic Type |
| ---     | ---         | ---          |
| D       | Discover    | Broadcast    |
| O       | Offer       | Unicast      |
| R       | Request     | Broadcast    |
| A       | Acknowledge | Unicast      |

<br>

### DHCP Loadbalancing
~~~
!@D1
conf t
 ip dhcp excluded-address 10.2.1.1 10.2.1.100
 ip dhcp pool MGMTPOOL.COM
  network 10.2.1.0 255.255.255.0
  default-router 10.2.1.254
  domain-name MGMTPOOL.COM
  dns-server 10.2.1.133
  end
~~~

~~~
!@D2
conf t
 ip dhcp excluded-address 10.2.1.1 10.2.1.200
 ip dhcp pool MGMTPOOL.COM
  network 10.2.1.0 255.255.255.0
  default-router 10.2.1.254
  domain-name MGMTPOOL.COM
  dns-server 10.2.1.133
  end
~~~

&nbsp;
---
&nbsp;

### VLAN Assignment - Place PCs (P1, P2) on VLAN 10

<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>

&nbsp;
---
&nbsp;

### ANSWER

<details>
<summary>Show Answer</summary>
  
~~~
!@A1
conf t
 int e0/0
  switchport mode access
  switchport access vlan 10
  end
~~~

~~~
!@A2
conf t
 int e1/0
  switchport mode access
  switchport access vlan 10
  end
~~~

</details>

&nbsp;
---
&nbsp;

### DHCP Clients - Configure P1 & P2 to be a DHCP client.

<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>

&nbsp;
---
&nbsp;

### ANSWER

<details>
<summary>Show Answer</summary>

~~~
!@P1
conf t
 int e0/0
  no shut
  ip add dhcp
  end
~~~

~~~
!@P2
conf t
 int e1/0
  no shut
  ip add dhcp
  end
~~~

</details>

<br>

What IP addresses did P1 & P2 get?

~~~
!@P1 & P2
show ip int brief | ex una
~~~

<br>
<br>

---
&nbsp;

### 🎯 Exercise 02: Static IP addressing.

| Device | VLAN | Host Address      |
| ---    | ---  | ---               |
| S1     | 100  | 192.168.1.133 /27 |
| S2     | 20   | 10.2.2.133 /24    |

Configure S1 & S2 for IP addressing and VLAN assinment as specified on the table above.
Verify connectivity through the following:
- Make sure __S1__ is able to ping __D1__, __D2__, __A1__, & __A2__ on __VLAN 100__
- Make sure __S2__ is able to ping __D1__ & __D2__ on __VLAN 20__

~~~
!@S1
conf t



  end


!@D1
conf t



  end


!@S2
conf t



  end


!@D2
conf t
 


  end
~~~

&nbsp;
---
&nbsp;

### ANSWER

<details>
<summary>Show Answer</summary>
  
~~~
!@S1
conf t
 int e1/0
  ip add 192.168.1.133 255.255.255.224
  no shut
  end
~~~

~~~
!@D1
conf t
 int e1/0
  switchport mode access
  switchport access vlan 100
  end
~~~

~~~
!@S2
conf t
 int e1/0
  ip add 10.2.2.133 255.255.255.0
  no shut
  end
~~~

~~~
!@D2
conf t
 int e1/0
  switchport mode access
  switchport access vlan 20
  end
~~~

</details>

<br>
<br>

---
&nbsp;

## 🔀 Static & Default Routing
*What is the normal behavior for network connectivity?*

<br>

~~~
!@R1
ping 10.1.1.2
vs
ping 10.1.1.5
~~~

Is the result normal? 

<br>

### Static Routing Configuration
Syntax:
`ip route [Destination IP]  [Network/Host Mask]  [Exit Interface / Nex-hop]`

<br>

What is a next-hop?

<br>

~~~
!@cmd
tracert 8.8.8.8

Tracing route to 8.8.8.8 over a maximum of 30 hops
  1     2 ms     1 ms     1 ms  192.168.1.1
  2     5 ms     6 ms     5 ms  100.83.0.1
  3     6 ms    11 ms     7 ms  122.2.203.6
  4    12 ms     6 ms     7 ms  210.213.130.15
  5    66 ms    62 ms    49 ms  142.250.175.196
  6     6 ms     6 ms     6 ms  142.251.251.47
  7     8 ms     5 ms     7 ms  142.250.58.243
  8     6 ms    10 ms    10 ms  8.8.8.8
~~~

<br>

Next-hop = 

<br>

~~~
!@R1
conf t
 ip route 10.1.1.5 255.255.255.255 10.1.1.2
 end
ping 10.1.1.5
~~~

<br>
<br>

---
&nbsp;

### 🎯 Exercise 03: Configure a static route on R2 destined for R3's e1/2 interface.
~~~
!@R2
conf t
 ip route __.__.__.__  __.__.__.__  __.__.__.__
 end
~~~

<br>
<br>
<br>
<br>

&nbsp;
---
&nbsp;

### ANSWER

<details>
<summary>Show Answer</summary>

~~~
!@R2
conf t
 ip route 10.1.1.9 255.255.255.255 10.1.1.6
 end
~~~

</details>

<br>
<br>

---
&nbsp;

### 🎯 Exercise 04: Configure a static route on R1 destined for R3's e1/1 interface.
~~~
!@R1
conf t
 ip route __.__.__.__  __.__.__.__  __.__.__.__
 end
~~~

<br>
<br>
<br>
<br>

&nbsp;
---
&nbsp;

### ANSWER

<details>
<summary>Show Answer</summary>

~~~
!@R1
conf t
 ip route 10.1.1.6 255.255.255.255 10.1.1.2
 end
~~~

<br>

__Routing must be two way__

~~~
!@R3
conf t
 ip route 10.1.1.1 255.255.255.255 10.1.1.5
 end
~~~

</details>

<br>
<br>

---
&nbsp;

### Host Route vs Network Route

### 🎯 Exercise 05: Review. Find the network of the following IP addresses:
| Network          | Host IP           |
| ---              | ---               |
|                  | 10.1.100.79 /18   |
|                  | 172.16.145.18 /20 |
|                  | 192.168.1.205 /30 | 

<br>
<br>

&nbsp;
---
&nbsp;

### ANSWER

<details>
<summary>Show Answer</summary>
	
| Network           | Host IP           |
| ---               | ---               |
| 10.1.64.0 /18     | 10.1.100.79 /18   |
| 172.16.144.0 /20  | 172.16.145.18 /20 |
| 192.168.1.204 /30 | 192.168.1.205 /30 | 
 
</details>

<br>
<br>

__Configure a Network route on R3 destined for R1 & R2's connected network.__

<br>

~~~
!@R3
show ip route static
~~~

<br>

Check the Network Mask of an interface: 3 ways
~~~
!@R1
show run
show int e1/0
show ip route 
~~~

~~~
!@R3
show ip route static
conf t
 ip route 10.1.1.0 255.255.255.252 10.1.1.5
 end
show ip route static
~~~

<br>
<br>

---
&nbsp;

__Configure R1 to be able to reach R4__

~~~
!@R1
conf t
 ip route 10.1.1.8 255.255.255.252 10.1.1.2
 end 
~~~

<br>

Verify:
~~~
!@R1
ping 10.1.1.9

vs

ping 10.1.1.10
~~~

<br>
<br>

---
&nbsp;

### 🎯 Exercise 07: Configure a static network route on R4 destined to R1's e1/0 interface
~~~
!@R4
conf t
 ip route 10.1.1.__ 255.255.255.252 10.1.1.__
 end
~~~

<br>
<br>

&nbsp;
---
&nbsp;

### ANSWER

<details>
<summary>Show Answer</summary>

~~~
!@R4
conf t
 ip route 10.1.1.0 255.255.255.252 10.1.1.9
 end
~~~
 
<br>
<br>

The next-hop device must also know how to route the packet
	
~~~
!@R2
conf t
 ip route 10.1.1.8 255.255.255.252 10.1.1.6
 end
~~~

<br>
<br>

R4 & R1 can now ping, but that doesn't mean they can ping the network of R3 & R2.

~~~
!@R4
conf t
 ip route 10.1.1.4 255.255.255.252 10.1.1.9
 end
~~~

</details>

<br>
<br>

---
&nbsp;

### How devices forward IP Packets.

![RST_IPv4](img/OSPF_only.png)


<br>
<br>

---
&nbsp;

### Static Route via Exit Interface

Configure a static host route on R3, destined for R4's 10.1.4.9 IP using both a next-hop address and interface.

~~~
!@R3
conf t
 ip route 10.1.4.9 255.255.255.255 e1/2 10.1.1.10
 end
~~~

<br>
<br>

---
&nbsp;

## 🔀 Default Route & Floating Static Route
~~~
!@cmd
route print
~~~

__Administrative Distance__ - Trustworthiness & Reliability of a Route Source

| AD Value | Trust Value               |
| ---      | ---                       |
| 0        | Most Trusted              |
| 1 - 254  | Lower Value, Higher Trust |
| 255      | Untrusted, Discarded      |

<br>

~~~
!@A1
conf t
 ip route 0.0.0.0 0.0.0.0 192.168.1.129 1
 ip route 0.0.0.0 0.0.0.0 192.168.1.130 10
 end
~~~

<br>

The Primary link went down:
~~~
!@A1
show ip route static
conf t
 no ip route 0.0.0.0 0.0.0.0 192.168.1.129 1
 end
show ip route static
~~~

<br>

The Primary link has been fixed
~~~
!@A1
conf t
 ip route 0.0.0.0 0.0.0.0 192.168.1.129 1
 end
show ip route static
~~~

<br>
<br>

---
&nbsp;

### 🎯 Exercise 08: Configure default routes on A2 with the following settings:
- __D2__ must be the __primary gateway__
- __D1__ must be the __secondary gateway__
- The __AD__ must have a difference of __10__

~~~
!@A2
conf t
 ip route 0.0.0.0 0.0.0.0 192.168.1.__  __
 ip route 0.0.0.0 0.0.0.0 192.168.1.__  __
 end
~~~

<br>
<br>

&nbsp;
---
&nbsp;

### ANSWER

<details>
<summary>Show Answer</summary>

~~~
!@A2
conf t
 ip route 0.0.0.0 0.0.0.0 192.168.1.130  1
 ip route 0.0.0.0 0.0.0.0 192.168.1.129  10
 end
~~~

</details>

<br>
<br>

---
&nbsp;

## Path Selection Process : Longest Prefix Match
1. __Longest Prefix Match (LPM)__  
2. &nbsp;
3. &nbsp;

<br>

~~~
!@P1
conf t
 ip route 192.168.1.128 255.255.255.224 10.2.1.1
 end
ping 192.168.1.129
~~~

<br>

__Routing Policies__, configure routing with the __least hop count possible__.

<br>

Verify:

~~~
!@P1
traceroute 192.168.1.129
traceroute 192.168.1.130
traceroute 192.168.1.131
traceroute 192.168.1.132
~~~

<br>

Why does P1 need to take 2 hop counts to reach D2's VLAN 100?

<br>

Configure a host static route that takes advantage of the longest prefix rule to allow P1 to go directly to D2 instead of D1.
~~~
!@P1
conf t
 ip route 192.168.1.130 255.255.255.255 10.2.1.2
 end
~~~

<br>

Verify:
~~~
!@P1
show ip route static

traceroute 192.168.1.129
traceroute 192.168.1.131
traceroute 192.168.1.132

vs

traceroute 192.168.1.130
~~~

<br>

<details>
<summary>Why longest prefix?</summary>

### `1 1 1 1   1 1 1 1   .   1 1 1 1   1 1 1 1   .   1 1 1 1   1 1 1 1   .   1 1 1 0   0 0 0 0`
### `1 1 1 1   1 1 1 1   .   1 1 1 1   1 1 1 1   .   1 1 1 1   1 1 1 1   .   1 1 1 1   1 1 1 1`

</details>

&nbsp;
---
&nbsp;

### Exam Question: Which Route will P1 use to reach 192.168.1.130 ?
~~~
S*    0.0.0.0/0 [254/0] via 10.2.1.254
      10.0.0.0/8 is variably subnetted, 2 subnets, 2 masks

C        10.2.1.0/24 is directly connected, Ethernet0/0

L        10.2.1.101/32 is directly connected, Ethernet0/0
      192.168.1.0/24 is variably subnetted, 2 subnets, 2 masks

S        192.168.1.128/27 [1/0] via 10.2.1.1

S        192.168.1.130/32 [1/0] via 10.2.1.2
~~~

<br>
<br>

---
&nbsp;

### 🎯 Exercise 09: Configure static routes on P2, destined for VLAN 100 with the least hop counts possible to D1, D2, A1, and A2.

~~~
!@P2
conf t
 ip route 192.168.1.__  __.__.__.__  __.__.__.__
 ip route 192.168.1.__  __.__.__.__  __.__.__.__
 end
~~~

<br>
<br>

&nbsp;
---
&nbsp;

### ANSWER

<details>
<summary>Show Answer</summary>

~~~
!@P2
conf t
 ip route 192.168.1.128 255.255.255.224 10.2.1.2
 ip route 192.168.1.129 255.255.255.255 10.2.1.1
 end
~~~

</details>

<br>
<br>

---
&nbsp;

### 🎯 Excercise 10: Configure static routes to allow P1 to ping Google (8.8.8.8)
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>

<br>
<br>

---
&nbsp;

## 🔀 Dynamic Routing
1. IGP (Interior Gateway Protocol)
  - Link-state - __OSPF__ & __ISIS__
  - Distance Vector - __EIGRP__ & __RIP__

2. EGP (Exterior Gateway Protocol)
  - __BGP__ (Border Gateway Protocol)

<br>
<br>

~~~
!@D1,D2,R4
show version
~~~

<br>

If all Cisco, use __EIGRP__

&nbsp;
---
&nbsp;


## 🔀 EIGRP
Steps in configuring EIGRP
1. Decide on an ASN
2. Determine Connected Networks
3. Advertise

~~~
!@R4
conf t
 router eigrp 100
  no auto-summary
  network 10.1.4.8 0.0.0.3
  network 10.1.4.4 0.0.0.3
  end
~~~

~~~
!@D1
config t
 router eigrp 100
  no auto-summary
  network 10.1.4.4 0.0.0.3
  network 10.2.1.0 0.0.0.255
  network 10.2.2.0 0.0.0.255
  network 192.168.1.128 0.0.0.31
end
~~~

<br>
<br>

---
&nbsp;

### 🎯 Excercise 11: Configure EIGRP on D2. Advertise all connected routes.
~~~
!@D2
config t
 router ____  ____
  no auto-summary
  network __.__.__.__  __.__.__.__
  network __.__.__.__  __.__.__.__
  network __.__.__.__  __.__.__.__
  network __.__.__.__  __.__.__.__
  end
~~~

<br>
<br>

&nbsp;
---
&nbsp;

### ANSWER

<details>
<summary>Show Answer</summary>

~~~
!@D2
conf t
 router eigrp 100
  no auto-summary
  network 10.1.4.8 0.0.0.3
  network 10.2.1.0 0.0.0.255
  network 10.2.2.0 0.0.0.255
  network 192.168.1.128 0.0.0.31
  end
~~~

</details>

### OPTIONAL
### Named EIGRP / Multi Address-Family EIGRP
When you are using NEXUS, address family is required.

~~~
!@R4
conf t
 router eigrp CCNPLEVEL
  address-family ipv4 unicast autonomous-system 100
   network 10.1.4.8 0.0.0.3
   network 10.1.4.4 0.0.0.3
   end
~~~

~~~
!@D1
conf t
 router eigrp CCNPLEVEL
  address-family ipv4 unicast autonomous-system 100
   network 10.1.4.4 0.0.0.3
   network 10.2.1.0 0.0.0.255
   network 10.2.2.0 0.0.0.255
   network 192.168.1.128 0.0.0.31
   end
~~~

~~~
!@D2
conf t
 router eigrp CCNPLEVEL
  address-family ipv4 unicast autonomous-system 100
   network 10.1.4.8 0.0.0.3
   network 10.2.1.0 0.0.0.255
   network 10.2.2.0 0.0.0.255
   network 192.168.1.128 0.0.0.31
   end
~~~

&nbsp;
---
&nbsp;

### EIGRP Database
1. __`show ip eigrp neighbors`__ : Neighbor Table
2. __`show ip eigrp interfaces`__ : Interface Table
3. __`show ip eigrp topology`__ : Topology Table

&nbsp;
---
&nbsp;

## Path Selection Process : Admin Distance & Metric Cost
1. __Longest Prefix Match (LPM)__  
2. __Administrative Distance__
3. __Metric Cost__

~~~
!@R4
show ip route
~~~

<br>

| Legend | Routing Protocol | Administrative Distance | Metric |
| ---    | ---              | ---                     | ---    |
| C      | Connected        |                         |        |
| S      | Static           |                         |        |
| D      | EIGRP            |                         |        |

<br>
<br>

What makes __EIGRP__ a __Distance Vector Protocol__?
~~~
!@R4
show ip protocols
show ip eigrp topology
~~~

<br>
<br>

### EIGRP Metric
*EIGRP Metric Formula*

<br>

![RST_IPv4](img/EIGRP_only.png)

<br>

__EIGRP Path Selection:__

| Device | RD  | FD  | Metric Path |
| ---    | --- | --- | ---         |
| D1     |     |     |             |
| D2     |     |     |             |

<br>

1. Reported Distance (__RD__)  
2. Feasible Distance (__FD__)  
3. Successor (Primary : Lowest Cost)  
4. Feasible Successor (Backup)  

<br>

__Feasability Condition__ - An EIGRP route is a feasible successor route if the RD from the neighbor is less than the FD of the successor route.

&nbsp;
---
&nbsp;

### EIGRP Loadbalancing Unequal Cost Paths - Variance
~~~
!@R4
conf t
 router eigrp 100
  variance 2
  traffic-share balanced
  end
~~~

<br>

or 

<br>

~~~
!@R4
conf t
 router eigrp CCNPLEVEL
  address-family ipv4 unicast autonomous-system 100
   topology base
    variance 2
    traffic-share balanced
    end
~~~

<br>
<br>

---
&nbsp;

### Review

Path Selection Process
1. &nbsp;
2. &nbsp;
3. &nbsp;

<br>

### Exam Question: When the following command was entered on R4, why did the route to 10.2.1.0 changed from D to S
~~~
!@R4
terminal length 0
show ip route
!
conf t
 ip route 10.2.1.0 255.255.255.0 10.1.4.6
 end
show ip route
~~~

<br>
<br>

---
&nbsp;

## 🔀 OSPF
*What device do you need to filter data entering your network? Firewall*

<br>

Which is the best firewall?
1. Palo Alto
2. Fortinet
3. Juniper
4. Cisco Firepower

<br>

What Routing protocol to use if __Multi-Vendor__? __OSPF__

<br>
<br>

### Single Area OSPF
Advertise Connected Routes:
~~~
!@R3
show ip route | inc C
~~~

~~~
!@R3
conf t
 router ospf 1
  router-id 3.3.3.3
  network 3.3.3.3 0.0.0.0 area 0
  network 10.1.1.8 0.0.0.3 area 0
  network 10.1.1.4 0.0.0.3 area 0
  end
~~~

<br>
<br>

---
&nbsp;

### 🎯 Excercise 12: Configure OSPF on R4 with the following settings:
- Process ID must be 1
- Advertise all connected routes that belong to OSPF area 0
- All of R4's interface belongs to Area 0
- Set R4's router id for OSPF as its loopback 4 IP

~~~
!@R4
conf t
 router ___  __
  router-id __.__.__.__
  network __.__.__.__  __.__.__.__ area __
  network __.__.__.__  __.__.__.__ area __
  end
~~~

<br>
<br>

&nbsp;
---
&nbsp;

### ANSWER

<details>
<summary>Show Answer</summary>

~~~
!@R4
conf t
 router ospf 1
  router-id 4.4.4.4
  network 4.4.4.4 0.0.0.0 area 0
  network 10.1.1.8 0.0.0.3 area 0
  end
~~~

</details>

<br>
<br>

---
&nbsp;

### 🎯 Excercise 13: Configure OSPF on R2 with the following settings:
- Process ID must be 1
- Advertise all connected routes that belong to OSPF area 0
- All of R2's interface belongs to Area 0
- Set R2's router id for OSPF as its loopback 2 IP

~~~
!@R2
conf t





  end
~~~

<br>
<br>

&nbsp;
---
&nbsp;

### ANSWER

<details>
<summary>Show Answer</summary>
	
~~~
!@R2
conf t
 router ospf 1
  router-id 2.2.2.2
  network 2.2.2.2 0.0.0.0 area 0
  network 10.1.1.0 0.0.0.3 area 0
  network 10.1.1.4 0.0.0.3 area 0
  end
~~~

</details>

<br>
<br>

---
&nbsp;

### OSPF Interface-specific network advertisement.
~~~
!@R1
conf t
 router ospf 1
  router-id 1.1.1.1
  exit
 int lo1
  ip ospf 1 area 0
  exit
 int e1/0
  ip ospf 1 area 0
  end
~~~

&nbsp;
---
&nbsp;

### OSPF Database
1. __`show ip ospf neighbors`__ : Neighbor Table
2. __`show ip ospf interface brief`__ : Interface Table
3. __`show ip ospf topology-info`__ : Topology Table

&nbsp;
---
&nbsp;

__What makes a dynamic routing protocol?__

~~~
!@R4
conf t
 int lo4
  shut
  end
~~~

~~~
!@R1
show ip route ospf
show ip ospf route
~~~

<br>

Bring back Loopback 4.4.4.4

<br>

~~~
!@R4
conf t
 int lo4
  no shut
  end
~~~

&nbsp;
---
&nbsp;

### Capture Hello Packets
~~~
!@R4
conf t
 int e3/3
  no shut
  ip add 208.8.8.100 255.255.255.0
  ip ospf 1 area 0
  exit
 router eigrp 100
  network 208.8.8.0 0.0.0.255
  end
~~~

<br>

__WireShark__ - Capture Packets from __VMNet8__ & filter __OSPF__  

<br>

## Job Interview Question.
### What are the contents of an OSPF Hello Packet?

<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>

<details>
<summary>Show Answer</summary>
	
- Router ID/Source OSPF Router
- Area ID
- Subnet Mask
- Authentication Type

- Hello Timer: 10
- Dead Timer: 40
- Designated Router
- Backup Designated Router

</details>

&nbsp;
---
&nbsp;

### Link-State Routing Protocol
__LSU__ - Link-State Updates  
__LSA__ - Link-State Advertisement  

<br>

- Type 1 LSA - (__O__) Router LSA : Router info
- Type 2 LSA - (__O__) Network LSA : via DR/BDR Network Routes
- Type 3 LSA - (__O IA__) Summary LSA
- Type 5 LSA - (__O E2__) AS-External LSA

<br>

~~~
!@EDGE
conf t
 int lo#$34T#
  int #$34T#.#$34T#.#$34T#.#$34T# 255.255.255.255
  ip ospf 1 area #$34T#
  end
clear ip ospf process
yes
~~~

~~~
!@R3
show ip ospf database
show ip ospf database network
~~~

&nbsp;
---
&nbsp;

### OSPF States
D: __Down__ - The initial state where no hello packets have been received from a neighbor  
I: __Init__ - A hello packet has been received from a neighbor, but that neighbor's Router ID was not included in the hello packet, indicating a lack of bidirectional communication  
T: __Two-way__ - Bidirectional communication is established, as both routers have received each other's Router IDs in hello packets. DR/BDR Election occurs.  
E: __Exstart__ - Routers determine who will be the master and who will be the slave for the upcoming database exchange. The router with the higher Router ID becomes the master and begins the exchange of Database Description (DBD) packets, synchronizing sequence numbers.  
E: __Exchange__ - Routers exchange DBD packets to describe their Link State Databases (LSDBs). They compare the contents and identify any missing link-state information  
L: __Loading__ - Routers request the missing link-state information by sending Link-State Requests (LSRs). They then receive Link-State Updates (LSUs) and acknowledge them with Link-State Acknowledgements (LSAs)  
F: __Full__ - the LSDBs are fully synchronized and identical between the adjacent routers. The routers have all the necessary information to form a complete network map and are ready to share routing data  

<br>

Attempt to view OSPF States

~~~
!@R2 & R1
clear ip ospf process
yes
show ip ospf neighbor
~~~

<br>
<br>

---
&nbsp;

### OSPF Network Types and Priorities.
### 🎯 Excercise 14: Ensure R3 is the DR for all its connected networks by completing the following tasks:
- Eliminate the need for a DR/BDR election between R4 & R3
- Configure R1 to be ineligible to become a DR/BDR
- Configure R2 with the highest priority on its e1/2 interface.

~~~
!@R4
conf t
 int e1/2
  ip ospf network point-to-point
  end
~~~

~~~
!@R3
conf t
 int e1/2
  ip ospf network point-to-point
  end
~~~

~~~
!@R2
conf t
 int e1/2
  ip ospf priority 255
  end
~~~

~~~
!@R1
conf t
 int e1/0
  ip ospf priority 0
  end
~~~

<br>

Verify:
~~~
!@R4,R3,R2,R1
show ip ospf neighbor
~~~

<br>
<br>

---
&nbsp;

### Neighborship vs Adjacency
- Same Area
- Same Subnet Mask/Network
- Same Network Type
- Same Hello Interval
- Same Dead Interval

<br>

1. __Mismatched Network Type__

~~~
!@R3
conf t
 int e1/2
  no ip ospf network point-to-point
  end
show ip ospf neighbor
clear ip ospf process
yes
~~~

~~~
!@R4
show ip route ospf
~~~

~~~
!@R3 & R4
show ip ospf int e1/2
~~~

<br>

Determine the issue why R3 & R4 fail to form an adjacency:

<br>
<br>

Fix the adjacency:

~~~
!@R3
conf t
 int e1/2
  ip ospf network point-to-point
  end
show ip ospf neighbor
clear ip ospf process
yes
~~~

&nbsp;
---
&nbsp;

2. __Mismatched Hello & Dead Timers__
~~~
!@R2
conf t
 int e1/2
  ip ospf hello-interval 20
  ip ospf dead-interval 60
  end
show ip ospf neighbor
clear ip ospf process
yes
~~~

~~~
!@R2
show ip ospf int e1/2
~~~

~~~
!@R1
show ip ospf int e1/0
~~~

<br>

Determine the issue why R2 & R1 fail to form an adjacency:

<br>
<br>

Fix the adjacency:
~~~
!@R2
conf t
 int e1/2
  ip ospf hello-interval 10
  ip ospf dead-interval 40
  end
show ip ospf neighbor
clear ip ospf process
~~~

<br>
<br>

---
&nbsp;

### OSPF Passive-Interface
Configure loopback interfaces to not send hello packets

~~~
!@R1
conf t
 router ospf 1
  passive-interface lo1
  end
~~~

~~~
!@R2
conf t
 router ospf 1
  passive-interface lo2
  end
~~~

~~~
!@R3
conf t
 router ospf 1
  passive-interface lo3
  end
~~~

~~~
!@R4
conf t
 router ospf 1
  passive-interface lo4
  end
~~~

<br>
<br>

---
&nbsp;

### OSPF & EIGRP Redistribution
~~~
!@R4
config T
 router eigrp 100
  redistribute ospf 1 metric 10000 100 255 1 1500
  exit
 router ospf 1
  redistribute eigrp 100 subnets
end
~~~

<br>

or

<br>

~~~
!@R4
conf t
 router eigrp CCNPLEVEL
  address-family ipv4 unicast autonomous-system 100
   topology base
    redistribute ospf 1 metric 10000 100 255 1 1500
	exit
   exit
  exit
 router ospf 1
  redistribute eigrp 100 subnets
    end
~~~

&nbsp;
---
&nbsp;

## Path Selection Process : Admin Distance & Metric Cost
1. __Longest Prefix Match (LPM)__  
2. __Administrative Distance__
3. __Metric Cost__

<br>

| Legend | Routing Protocol | Administrative Distance | Metric |
| ---    | ---              | ---                     | ---    |
| C      | Connected        |                         |        |
| S      | Static           |                         |        |
| D      | EIGRP            |                         |        |
| D EX   | External EIGRP   |                         |        |
| O      | OSPF             |                         |        |
| O E2   | External T5 OSPF |                         |        |

~~~
!@R4, D1, R3
show ip route
~~~

<br>
<br>

### OSPF Metric Cost 
Interface Cost = Reference Bandwidth / Interface Bandwidth
~~~
!@R3
show ip ospf | inc band
~~~

~~~
!@R1,R2,R3,R4
conf t
 router ospf 1
  auto-cost reference-bandwidth 100000
  end
~~~

<br>
<br>

---
&nbsp;

### Route Summarization
~~~
!@R2
conf t
 int lo8
  ip add 10.10.8.1 255.255.255.0
  ip ospf 1 area 12
 int lo9
  ip add 10.10.9.1 255.255.255.0
  ip ospf 1 area 12
 int lo10
  ip add 10.10.10.1 255.255.255.0
  ip ospf 1 area 12
 int lo11
  ip add 10.10.11.1 255.255.255.0
  ip ospf 1 area 12
 int lo33
  ip add 10.10.33.1 255.255.255.128
  ip ospf 1 area 12
 int lo34
  ip add 10.10.33.129 255.255.255.128
  ip ospf 1 area 12
 int lo35
  ip add 10.10.34.1 255.255.255.128
  ip ospf 1 area 12
 int lo36
  ip add 10.10.34.129 255.255.255.128
  ip ospf 1 area 12
  exit
 router ospf 1
  passive-interface lo8
  passive-interface lo9
  passive-interface lo10
  passive-interface lo11
  passive-interface lo33
  passive-interface lo34
  passive-interface lo35
  passive-interface lo36
  end
~~~

<br>

Steps to summarize routes for OSPF
1. Determine the octet in which the Networks increment.
10.10.8.0
10.10.9.0
10.10.10.0
10.10.11.0

= 3rd Octet

<br>

2. From the specified octet, find the difference between the first network (8) and the last (11).
11 - 8 = 3

<br>

3. Based on the difference (3), determine the next closes i.
The closest to 3 is 4i

<br>

4. Determine the new slash based on the chosen i (4i) and the octet (3rd) where the networks increments.
(3rd Octet, 4i) = /22

<br>

5. Finally, apply the new CIDR (/22) to the lowest network (10.10.8.0). Then, find the network.
= 10.10.8.0/22

<br>

~~~
!@R2
conf t
 router ospf 1
  area 12 range 10.10.8.0 255.255.252.0
  end
~~~

<br>
<br>

---
&nbsp;

### 🎯 Excercise 15: Summarize routes from loopback 33 - loopback 36
~~~
!@R2
conf t
 router ospf __
  area __ range __.__.__.__  __.__.__.__
  end
~~~

<br>
<br>

&nbsp;
---
&nbsp;

### ANSWER

<details>
<summary>Show Answer</summary>
	
~~~
!@R2
conf t
 router ospf 1
  area 12 range 10.10.32.0 255.255.252.0 
  end
~~~

</details>

<br>

Remove All summarizations
~~~
!@R2
conf t
 router ospf 1
  no area 12 range 10.10.8.0 255.255.252.0
  no area 12 range 10.10.32.0 255.255.252.0
  end
~~~

<br>
<br>

---
&nbsp;

### 🎯 Excercise 16: Summarize both summarized routes

<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>

<br>
<br>

&nbsp;
---
&nbsp;

### ANSWER

<details>
<summary>Show Answer</summary>
	
~~~
!@R2
conf t
 router ospf 1
  area 12 range 10.10.0.0 255.255.192.0
  end
~~~

</details>

<br>
<br>

~~~
!@R4
show ip ospf database
~~~

<br>
<br>

---
&nbsp;

### BGP
Hurrican AS Number
- Globe
- PLDT
- Converge

<br>

R1 = ASN 1  
I1 & I4(GOOGLE DNS) = ASN 45  
I2 = ASN 2  
I3 = ASN 1  

<br>
<br>

~~~
!@R1
conf t
 router bgp 1
  bgp log-neighbor-changes
   neighbor 208.8.8.4 remote-as 45
   neighbor 207.7.7.2 remote-as 2
   neighbor 209.9.9.3 remote-as 3
   address-family ipv4
	neighbor 208.8.8.4 activate
    neighbor 207.7.7.2 activate
    neighbor 209.9.9.3 activate
    network 207.7.7.0 mask 255.255.255.0
    network 208.8.8.0 mask 255.255.255.0
    network 209.9.9.0 mask 255.255.255.0
    end
~~~

~~~
!@I1 - CONVERGE
conf t
 router bgp 45
  bgp log-neighbor-changes
  neighbor 24.2.4.2 remote-as 2
  neighbor 45.4.5.5 remote-as 45
  neighbor 208.8.8.1 remote-as 1
  address-family ipv4
   neighbor 24.2.4.2 activate
   neighbor 45.4.5.5 activate
   neighbor 208.8.8.1 activate
   network 208.8.8.0 mask 255.255.255.0
   network 24.2.4.0 mask 255.255.255.0
   network 44.44.44.44 mask 255.255.255.255
   network 45.4.5.0 mask 255.255.255.0
   end
~~~

<br>
<br>

---
&nbsp;

### 🎯 Excercise 17: Configure BGP on I3 - Globe with the following:
- Advertise all connected networks
- Set the ASN number to ASN 3

~~~
!@I3 - GLOBE
conf t
 router bgp __
  bgp log-neighbor-changes
  ______  __.__.__.__ remote-as __
  ______  __.__.__.__ remote-as __
  ______  __.__.__.__ remote-as __
  address-family __
   ______  __.__.__.__ activate
   ______  __.__.__.__ activate
   ______  __.__.__.__ activate
   ______  __.__.__.__ mask __.__.__.__
   ______  __.__.__.__ mask __.__.__.__
   ______  __.__.__.__ mask __.__.__.__
   ______  __.__.__.__ mask __.__.__.__
   end
~~~

<br>
<br>

&nbsp;
---
&nbsp;

### ANSWER

<details>
<summary>Show Answer</summary>

~~~
!@I3 - GLOBE
conf t
 router bgp 3
  bgp log-neighbor-changes
  neighbor 32.3.2.2 remote-as 2
  neighbor 35.3.5.5 remote-as 45
  neighbor 209.9.9.1 remote-as 1
  address-family ipv4
   neighbor 32.3.2.2 activate
   neighbor 35.3.5.5 activate
   neighbor 209.9.9.1 activate
   network 209.9.9.0 mask 255.255.255.0
   network 32.3.2.0 mask 255.255.255.0
   network 33.33.33.33 mask 255.255.255.255
   network 35.3.5.0 mask 255.255.255.0
   end
~~~

</details>

<br>
<br>

~~~
!@I4 - GOOGLE
config t
 router bgp 45
  bgp log-neighbor-changes
  neighbor 25.2.5.2 remote-as 2
  neighbor 35.3.5.3 remote-as 3
  neighbor 45.4.5.4 remote-as 45
  address-family ipv4
   neighbor 25.2.5.2 activate
   neighbor 35.3.5.3 activate
   neighbor 45.4.5.4 activate
   network 8.8.8.8 mask 255.255.255.255
   network 55.55.55.55 mask 255.255.255.255
   network 25.2.5.0 mask 255.255.255.0
   network 35.3.5.0 mask 255.255.255.0
   network 45.4.5.0 mask 255.255.255.0
   end
~~~

<br>
<br>

---
&nbsp;

### 🎯 Excercise 18: Configure BGP on I2(PLDT). Set the ASN number to 2.
- Advertise the loopback IP

~~~
!@I2 - PLDT
config t
 router bgp __
 bgp log-neighbor-changes
 neighbor __.__.__.__ remote-as __
 neighbor __.__.__.__  remote-as __
 neighbor __.__.__.__  remote-as __
 neighbor __.__.__.__  remote-as __
 address-family __
  neighbor __.__.__.__  ____
  neighbor __.__.__.__  ____
  neighbor __.__.__.__  ____
  neighbor __.__.__.__  ____
  network __.__.__.__ mask __.__.__.__
  network __.__.__.__ mask __.__.__.__
  network __.__.__.__ mask __.__.__.__
  network __.__.__.__ mask __.__.__.__
  network __.__.__.__ mask __.__.__.__
  end
~~~

<br>
<br>

&nbsp;
---
&nbsp;

### ANSWER

<details>
<summary>Show Answer</summary>

~~~
!@I2 - PLDT
config t
 router bgp 2
 bgp log-neighbor-changes
 neighbor 24.2.4.4 remote-as 45
 neighbor 25.2.5.5 remote-as 45
 neighbor 32.3.2.3 remote-as 3
 neighbor 207.7.7.1 remote-as 1
 address-family ipv4
  neighbor 24.2.4.4 activate
  neighbor 25.2.5.5 activate
  neighbor 32.3.2.3 activate
  neighbor 207.7.7.1 activate
  network 207.7.7.0 mask 255.255.255.0
  network 22.22.22.22 mask 255.255.255.255
  network 24.2.4.0 mask 255.255.255.0
  network 25.2.5.0 mask 255.255.255.0
  network 32.3.2.0 mask 255.255.255.0
  end
~~~

</details>

<br>
<br>

Verify:

~~~
!@I2 - PLDT
show bgp summary
~~~

<br>
<br>

---
&nbsp;

### BGP - OSPF Redistribution (Default Route Propagation)
~~~
!@R1
conf t
 router ospf 1
  default-information originate always
  end
~~~

~~~
!@R1
show ip route
~~~

&nbsp;
---
&nbsp;

## Path Selection Process : Admin Distance & Metric Cost
1. __Longest Prefix Match (LPM)__  
2. __Administrative Distance__
3. __Metric Cost__

<br>

| Legend | Routing Protocol | Administrative Distance | Metric |
| ---    | ---              | ---                     | ---    |
| C      | Connected        |                         |        |
| S      | Static           |                         |        |
| D      | EIGRP            |                         |        |
| D EX   | External EIGRP   |                         |        |
| O      | OSPF             |                         |        |
| O E2   | External T5 OSPF |                         |        |
| B      | Internal BGP     |                         |        |
| B      | External BGP     |                         |        |

<br>

~~~
!@R1, I1 - CONVERGE
show ip route
~~~

<br>
<br>

---
&nbsp;

### NAT
~~~
INSIDE GLOBAL     INSIDE LOCAL         OUTSIDE LOCAL      OUTSIDE GLOBAL
~~~

Step 1: Define INSIDE and OUTSIDE

~~~
!@R1
conf t
 int range e1/1-3
  ip nat outside
  exit
 int e1/0
  ip nat inside
  end
~~~

<br>

Step 2: Create an ACL to match traffic

~~~
!@R1
conf t
 access-list 1 permit 10.0.0.0 0.255.255.255
 access-list 1 permit 172.16.0.0 0.15.255.255
 access-list 1 permit 192.168.0.0 0.0.255.255
 end
~~~

<br>

Step 3: Configure desired NAT

### Static NAT or 1:1
~~~
!@R1
conf t
 ip nat inside source static 10.1.4.6 209.9.9.1 
 ip nat inside source static 10.1.1.2 209.9.9.2
 ip nat inside source static 10.1.1.10 209.9.9.3
 end
show ip nat translations
~~~

<br>

10.1.4.6 = D1
10.1.1.2 = R2
10.1.1.10 = R4

~~~
!@D1, R2, R4
ping 8.8.8.8
~~~

Can all of them ping 8.8.8.8? If not, explain why.

<br>

~~~
!@R1
clear ip nat translation *
conf t
 no ip nat inside source static 10.1.1.10 209.9.9.3
 ip nat inside source static 10.1.1.10 209.9.9.4
 end
show ip nat translations
~~~


Exercise 18: Configure Static NAT to output the following:

Pro  INSIDE GLOBAL    INSIDE LOCAL 
---  207.7.7.1        192.168.1.131
icmp 207.7.7.1:x      192.168.1.131:x
---  208.8.8.45       10.1.4.10
icmp 208.8.8.45:x     10.1.4.10:x
---  209.9.9.99       3.3.3.3
icmp 209.9.9.99:x     3.3.3.3:x

Tip:

192.168.1.131 = A1
10.1.4.10 = D2
3.3.3.3 = R3

!@R1
conf t
 ip nat inside source static 192.168.1.131 207.7.7.1
 ip nat inside source static 10.1.4.10 208.8.8.45
 ip nat inside source static 3.3.3.3 209.9.9.99
 end 


Verify with a ping to 8.8.8.8 on the 3 devices, 
then use the show command to reveal translated IPs on R1.



!@R1
conf t
 ip nat inside source static 192.168.1.131 207.7.7.1
 ip nat inside source static 10.1.4.10 208.8.8.45
 ip nat inside source static 3.3.3.3 209.9.9.99
 end 
show ip nat translations


Ans

!@R1
conf t
 ip nat inside source static 10.1.4.10 207.7.7.1
 end
show ip nat translations


---

Dynamic NAT or 1:Many

Create a pool of addresses

!@R1
conf t
 ip nat pool mynatpool 209.9.9.4 209.9.9.254 netmask 255.255.255.0
 ip nat inside source list 1 pool mynatpool
 end


Verify:

!@A2
ping 8.8.8.8



Exercise 19: Determine why D1 failed to ping 8.8.8.8 with a source IP of 10.2.1.1

!@D1
ping 8.8.8.8 source 10.2.1.1

Ans

R1 does not have a route for 10.2.1.0/24 network

SOLUTION
Either remove the static route from R4 to 10.2.1.0/24 network to prevent R4 from discarding the route learned via EIGRP

!@R4
conf t
 no ip route 10.2.1.0 255.255.255.0 10.1.4.6
 end
 
or

Redistribute static routes into OSPF

!@R4
conf t
 router ospf 1
  redistribute static subnets
  end




---

NAT Overloading or PAT

- Translate private ips to a single ip  using a unique port number.

!@R1
clear ip nat translation *
conf t
 no ip nat inside source list 1 pool mynatpool
 end


!@R1
conf t
 ip nat inside source list 1 interface e1/1 overload
 end



Exercise 20: Configure P1, P2, S1, & S2 to successfully ping 8.8.8.8

They do not have default routes

!@P1,P2
conf t
 ip route 0.0.0.0 0.0.0.0 10.2.1.1
 end


!@S1
conf t
 ip route 0.0.0.0 0.0.0.0 192.168.1.129
 end

!@S2
conf t
 ip route 0.0.0.0 0.0.0.0 10.2.2.2
 end

Why are end devices configured with default routes.






-----

IPv6

Does your device support IPv6?


What is a valid IPv6 address?


IPv6 compression rules

1. All zeroes on the left are ommitted.

:00a0:  >   :a0:

2. Subsequent zeroes turn into double colon.

:0000:0000:0000:00a0:  >  ::a0:

3. When there are two subsequent zeroes, the one with more zeroes gets turned into :
while the other zeroes becom :0:

:0000:0000:00a0:0000:0000:0000:  >  :0:0:a0::

4. When subsequent zeroes match on both sides, the one on the left turns into double colon.

:0000:0000:00a0:0000:0000:  >  ::a0:0:0:


Exercise 21: Compress IPv6 address

1. 000a:000c:0000:0000:0000:0000:0000:0000/64 =
	
2. 0000:0000:0000:0000:0000:0000:0000:0000/0 = 
			
3. fe80:0000:0000:0000:000a:0000:0000:000f/64 =
	
4. 2002:6500:0000:3000:0000:0000:0000:0000/64 = 
	
5. 0000:0000:0000:0000:0000:0000:0000:0001/128 = 
	
6. ff00:0000:0000:beef:a00a:0aa0:0000:0000/8 = 


---


IPv6 subnetting


8  4  2   1    8  4  2   1     8  4  2   1    8  4  2   1 


IPV6 SUBNETTING (HOSTS):
fec0:aabb:fafa:dada::/64 subnet for 48 users:
Convert:
S:
Ipasok:



IPV6 SUBNETTING (SUBNETS):
fec0:aabb:fafa:dada::/64 subnet to 22 offices/subnets:
Convert:  22 -> 5bits
Add: /64 + /5 = /69
Ipasok:







---


IPv6 Static & Default Routing



IPv6 Transition Technology



IPv6 autoconfig























---

IP SLA


conf t 
 ip sla 1
  icmp-echo 8.8.8.8
  frequency 10
 ip sla schedule 1 life forever start-time now
 end

TRACK

conf t
 track 1 ip sla 1 reachability 
 track 1 ip sla 1 state
  delay up 5
  delay down 10
 end

ROUTE-MAP

conf t
 route-map NAT-FAILOVER-PLDT permit 10
  match ip address 1
  set int e1/2
 route-map NAT-FAILOVER-GLOBE permit 20
  match ip address 1
  set int e1/3
  end
  
 route-map NAT-FAILOVER permit 10
  match track 1
  set int e1.2
  

  
















Route MAPS

!@R1
conf t
 access-list 10 permit 10.2.1.0 0.0.0.255
 access-list 20 permit 10.2.2.0 0.0.0.255
 access-list 30 permit 192.168.1.128 0.0.0.31
 
 ip nat pool CONVERGE 208.8.8.1 208.8.8.254 netmask 255.255.255.0
 ip nat pool PLDT 207.7.7.1 207.7.7.254 netmask 255.255.255.0
 ip nat pool GLOBE 209.9.9.1 209.9.9.254 netmask 255.255.255.0
 
 route-map RM_CONVERGE permit 10
  match ip address 10
  set ip nat pool CONVERGE
 route-map RM_PLDT permit 20
  match ip address 20
  set ip nat pool PLDT 
