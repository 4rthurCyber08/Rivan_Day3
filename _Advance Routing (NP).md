
<!-- Your monitor number = #$34T# -->


## ⛅ Warm Up for Day 3.

<br>

### 🔧 Physically Connect the following:
| Device   | Port       |  -  | Port   | Switch   |
| ---      | ---        | --- | ---    | ---      |
| PC       | TunayNaLAN |  -  | fa0/1  | CoreBABA |
| WLC      | PoE        |  -  | fa0/2  | CoreBABA |
| AP       | PoE        |  -  | fa0/4  | CoreBABA |
| CUCM     | fe0/0      |  -  | fa0/3  | CoreBABA |
| ePhone 1 | Network    |  -  | fa0/5  | CoreBABA |
| ePhone 2 | Network    |  -  | fa0/7  | CoreBABA |
| Cam6     | Eth        |  -  | fa0/6  | CoreBABA |
| Cam8     | Eth        |  -  | fa0/8  | CoreBABA |
| CoreTAAS | fa0/10     |  -  | fa0/10 | CoreBABA |
| CoreTAAS | fa0/11     |  -  | fa0/11 | CoreBABA |
| CoreTAAS | fa0/12     |  -  | fa0/12 | CoreBABA |


<br>
<br>

---
&nbsp;

### Dynamic Routing Protocols

Internal Gateway Protocols
1. Link-state - __OSPF__ & __ISIS__  
2. Distance Vector - __EIGRP__ & __RIP__

<br>

Exterior Gateway Protocols
1. __BGP__ - Border Gateway Protocol


<br>
<br>

---
&nbsp;


# EIGRP (Enhanced Interior Gateway Protocol)
Algorithm: __DUAL__ (Diffusing Update Algorithm)

<br>

Configure EIGRP
1. Decide on an ASN
2. Determine Networks to advertise


&nbsp;
---
&nbsp;


### Classic EIGRP
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
!@C1
config t
 router eigrp 100
  no auto-summary
  network 10.1.4.4 0.0.0.3
  network 10.2.1.0 0.0.0.255
  network 10.2.2.0 0.0.0.255
  network 192.168.1.128 0.0.0.31
  end
~~~

~~~
!@C2
conf t
 router eigrp 100
  no auto-summary
  network 10.1.4.8 0.0.0.3
  network 10.2.1.0 0.0.0.255
  network 10.2.2.0 0.0.0.255
  network 192.168.1.128 0.0.0.31
  end
~~~


&nbsp;
---
&nbsp;


## EIGRP Hello

| Network Type | Hello | Hold |
| ---          | ---   | ---  |
| Ethernet     | 5s    | 15s  |
| WAN          | 60s   | 180s |

<br>

### 1. __Hello__ - Discovers and maintains neighbor relationships.


<br>

__SPAN__
~~~
!@C1
conf t
 int e3/3
  no shut
  no switchport
  exit
 monitor session 1 source interface e1/1 both
 monitor session 1 destination interface e3/3
 end
~~~


&nbsp;
---
&nbsp;


### 2. __Update__ - Sends routing information when a new route appears or a metric changes.


<br>

~~~
!@R4
conf t
 router eigrp 100
  no network 10.1.4.4 0.0.0.3
  network 10.1.4.4 0.0.0.3
  end
~~~

<br>

__RSPAN__
~~~
!@C2
conf t
 vlan 10
  remote-span
  exit
 monitor session 1 source interface e1/1 both
 monitor session 1 destination remote vlan 10
 end
~~~

~~~
!@C1
conf t
 vlan 10
  remote-span
  exit
 no monitor session 1 source interface e1/1 both
 monitor session 1 source remote vlan 10
 end
~~~


&nbsp;
---
&nbsp;


### 3. __Query__ - Sent when a route is lost and the router asks neighbors for an alternative path.



&nbsp;
---
&nbsp;


### 4. __Reply__ - Response to a Query with route information.


<br>

~~~
!@C1
conf t
 int vlan 20
  shut
  no shut
  end
~~~


&nbsp;
---
&nbsp;


### 5. __ACK__ - Confirms receipt of reliable EIGRP packets (Update, Query, Reply).


<br>
<br>

---
&nbsp;


## Classic EIGRP Metric Calculation

$$
256 \times \left( \frac{10^7}{\text{Min.\ BW}} + \frac{\text{Total Delay}}{10} \right)
$$

<br>

~~~
!@R4
show ip route eigrp
~~~

<br>

From __R4__ to 10.2.1.0/24  

<br>

| Attribute | Value  |
| ---       | ---    |
| Min. BW   | 10_000 |
| Total DLY | 1_010  |

<br>

~~~
= 256 * { (10_000_000 / 10_000 kbps ) + [(R4 1000 usec + C1 10 usec) / 10] }
= 256 * { 1_000 + [(R4 1000 usec + C1 10 usec) / 10] }
= 256 * { 1_000 + [1010 / 10] }
= 256 * { 1_000 + 101 }
= 256 * 1_101
= 281_856
~~~


<br>
<br>

---
&nbsp;


### 🎯 Exercise 01: Compute for Classic EIGRP metric for the network 10.2.1.0/24 & 10.1.4.4/30 on R3

~~~
!@R4,R3
conf t
 router eigrp 100
  network 10.1.1.8 0.0.0.3
  end
~~~

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


### Named EIGRP or Multi Address-Family EIGRP
~~~
!@R3,R4,C1,C2
conf t
 no router eigrp 100
 end
~~~

<br>

~~~
!@R4
conf t
 router eigrp CCNPLEVEL
  address-family ipv4 unicast autonomous-system 100
   network 10.1.4.8 0.0.0.3
   network 10.1.4.4 0.0.0.3
   end
~~~

<br>

~~~
!@C1
conf t
 router eigrp CCNPLEVEL
  address-family ipv4 unicast autonomous-system 100
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


### 🎯 Exercise 02: Advertise all connected routes on C2 using Named EIGRP. Assign the same AS as C1.

~~~
!@C2
conf t
 router eigrp ____
  address-family ________________________
   network __.__.__.__   __.__.__.__

   end
~~~

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


## Named EIGRP Metric Calculation
  
__Classic Metric__

$$
256 \times \left( \frac{10^7}{\text{Min.\ BW}} + \frac{\text{Total Delay}}{10} \right)
$$

  
<br>


__Wide Metric__

$$
\left(
\frac{10^7 \cdot 65536}{\text{Min.\ BW}}
+
\frac{\text{Total Delay (psec)} \cdot 65536}{10^6}
\right)
$$


<br>
<br>


*Why Wide Metric?*  

1. __GigabitEthernet__:
   - Scaled bandwidth: 10_000_000 / 1_000_000 = 10
   - Scaled delay: 10 / 10 = 1
   - Composite metric: 10 + 1 * 256 = 2816

2. __10 GigabitEthernet__:
   - Scaled bandwidth: 10_000_000 / 10_000_000 = 1
   - Scaled delay: 10 / 10 = 1
   - Composite metric: 1 + 1 * 256 = 512

3. __20 GigabitEthernet__:
   - Scaled bandwidth: 10_000_000 / 20_000_000 = 0.5 (rounded to 0)
   - Scaled delay: 10 / 10 = 1
   - Composite metric: 0 + 1 * 256 = 256

4. __40 GigabitEthernet__:
   - Scaled bandwidth: 10_000_000 / 40_000_000 = 0.25 (rounded to 0)
   - Scaled delay: 10 / 10 = 1
   - Composite metric: 0 + 1 * 256 = 256


&nbsp;
---
&nbsp;


### Calculate From R4 to 10.2.1.0/24

| Attribute | Value  |
| ---       | ---    |
| Min. BW   | 10_000 |
| Total DLY | 1_010  |

<br>

~~~
BW = 10_000 kbps  
Delay = 1_010 usec > 1_010_000_000 psec (10^6)  


Throughput
 = (10^7 * 65_536) / 10_000
 = 655_360_000_000 / 10_000
 = 65_536_000
 
Latency
 = (1_010_000_000 * 65_536) / 10^6
 = 66_191_360_000_000 / 1_000_000
 = 66_191_360

Throughput + Latency
 = 65_536_000  +  66_191_360
 = 131_727_360
~~~


<br>
<br>


~~~
!@R4
show ip route eigrp
show ip protocols
~~~

~~~
Feasible Distance / Rib-Scale
 = 131_727_360 / 128
 = 1_029_120
~~~

<br>
<br>

---
&nbsp;


### 🎯 Exercise 03: Configure 10.1.49.0/24 network on A1 and advertise it via EIGRP. 
Determine the composite metric from R4 to A1's 10.1.49.0/24 network.

~~~
!@A1
conf t
 vlan 49
  name FINANCE
  exit
 int vlan 49
  no shut
  ip add 10.1.49.1 255.255.255.0
  bandwidth 10000000
  delay 1000
  exit
 !
 router eigrp CCNPLEVEL
  add ipv4 uni a 100
   network 192.168.1.128 0.0.0.31
   network 10.1.49.0 0.0.0.255
   end
~~~

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


### 🎯 Exercise 04: Configure 10.1.50.0/24 network on A2 and advertise it via EIGRP. 
Determine the composite metric from R4 to A2's 10.1.50.0/24 network.

~~~
!@A2
conf t
 vlan 50
  name SOC
  exit
 int vlan 50
  no shut
  ip add 10.1.50.1 255.255.255.0
  bandwidth 1000
  delay 500
  exit
 !
 router eigrp CCNPLEVEL
  add ipv4 uni a 100
   network 192.168.1.128 0.0.0.31
   network 10.1.50.0 0.0.0.255
   end
~~~

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


## EIGRP Path Selection
~~~
!@R4
show ip eigrp topology

P 10.2.2.0/24, 1 successors, FD is 131727360
        via 10.1.4.10 (131727360/1310720), Ethernet1/1
        via 10.1.4.6 (132382720/1966080), Ethernet1/0
~~~

<br>

| Reported Distance (Neighbor Cost) | Feasible Distance |
| ---                               | ---               |
| 1_310_720                         | 131_727_360       |
| 1_966_080                         | 132_382_720       |

<br>

1. Successor - Best Path
2. Feasible Successor - RD of Route < FD of Successor


<br>
<br>

---
&nbsp;


### 🎯 Exercise 05: Determine Successor and Feasible Successor from R4 to 10.1.51.0/24

~~~
!@A1
conf t
 vlan 51
  exit
 int vlan 51
  no shut
  ip add 10.1.51.3 255.255.255.0
  bandwidth 1000
  delay 100
  exit
 router eigrp CCNPLEVEL
  add ipv4 uni a 100
   network 10.1.51.0 0.0.0.255
   end
~~~

~~~
!@A2
conf t
 vlan 51
  exit
 int vlan 51
  no shut
  ip add 10.1.51.4 255.255.255.0
  bandwidth 10000
  delay 10
  exit
 router eigrp CCNPLEVEL
  add ipv4 uni a 100
   network 10.1.51.0 0.0.0.255
   end
~~~

~~~
!@C1
conf t
 vlan 51
  exit
 int vlan 51
  no shut
  ip add 10.1.51.1 255.255.255.0
  bandwidth 100
  delay 1000
  exit
 router eigrp CCNPLEVEL
  add ipv4 uni a 100
   network 10.1.51.0 0.0.0.255
   end
~~~

~~~
!@C2
conf t
 vlan 51
  exit
 int vlan 51
  no shut
  ip add 10.1.51.2 255.255.255.0
  bandwidth 1000
  delay 1000
  exit
 router eigrp CCNPLEVEL
  add ipv4 uni a 100
   network 10.1.51.0 0.0.0.255
   end
~~~

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


## EIGRP Unequal Cost Loadbalancing

~~~
!@C1
conf t
 int e2/0
  no sw
  no shut
  ip add 10.1.8.6 255.255.255.252
 !
 router eigrp CCNPLEVEL
  address-family ipv4 unicast a 100
   network 10.1.8.4 0.0.0.3
   end
~~~

~~~
!@C2
conf t
 int e2/1
  no sw
  no shut
  ip add 10.1.8.10 255.255.255.252
 !
 router eigrp CCNPLEVEL
  address-family ipv4 unicast a 100
   network 10.1.8.8 0.0.0.3
   end
~~~

~~~
!@R4
conf t
 int e2/0
  no shut
  ip add 10.1.8.5 255.255.255.252
  delay 800
 int e2/1
  no shut
  ip add 10.1.8.9 255.255.255.252
  delay 800
 !
 router eigrp CCNPLEVEL
  address-family ipv4 unicast a 100
   network 10.1.8.4 0.0.0.3
   network 10.1.8.8 0.0.0.3
   end
~~~


<br>
<br>


~~~
!@R4
conf t
 router eigrp CCNPLEVEL
  address-family ipv4 unicast a 100
   topology base
    variance 5   ! 1 default equal cost only
	end
~~~

<br>


$$
\text{FD}_{\text{candidate}} \le \text{FD}_{\text{successor}} \times \text{Variance}
$$



<br>
<br>

---
&nbsp;


## EIGRP Neighborship vs Adjacency

1. ASN Mismatch
~~~
!@R4
conf t
 router eigrp 200
  network 10.1.4.4 0.0.0.3
  end
~~~

~~~
!@C1
conf t
 router eigrp 100
  network 10.1.4.4 0.0.0.3
  end
~~~


<br>


2. Metric Weights

~~~
!@R4
conf t
 router eigrp 100
  metric weights 0 1 0 1 0 0  
  end
~~~


<br>


3. Wrong Network Advertisement
~~~
!@R4
conf t
 router eigrp 100
  network 10.1.4.0 0.0.0.31
  end
~~~

~~~
!@C1
conf t
 router eigrp 100
  network 10.1.4.0 0.0.0.15
  end
~~~


<br>
<br>

---
&nbsp;


# Open Shortest Path First (Multi-Area OSPF)

~~~
!@R3
conf t
 router ospf 1
  router-id 3.3.3.3
  network 3.3.3.3 0.0.0.0 area 0
  network 10.1.1.8 0.0.0.3 area 34
  network 10.1.1.4 0.0.0.3 area 0
  end
~~~

~~~
!@R4
conf t
 router ospf 1
  router-id 4.4.4.4
  network 4.4.4.4 0.0.0.0 area 34
  network 10.1.1.8 0.0.0.3 area 34
  end
~~~

~~~
!@R2
conf t
 router ospf 1
  router-id 2.2.2.2
  exit
 int lo2
  ip ospf 1 area 0
  exit
 int e1/1
  ip ospf 1 area 0
  exit
 int e1/2
  ip ospf 1 area 12
  end
~~~

~~~
!@R1
conf t
 router ospf 1
  router-id 1.1.1.1
  exit
 int lo1
  ip ospf 1 area 12
  exit
 int e1/0
  ip ospf 1 area 12
  end
~~~


<br>
<br>

---
&nbsp;


## OSPF Network Types and Priorities.

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
<br>
---
&nbsp;


## OSPF Hello Packet
__SPAN__
~~~
!@CoreBABA
conf t
 monitor session 1 source interface g0/1
 monitor session 1 destination interface fa0/1
 end
~~~

~~~
!@R4
conf t
 int e3/3
  no shut
  ip add dhcp
  ip ospf 1 area 34
  exit
 end
~~~

<br>

| OSPF Hello          | Value |
| ---                 | ---   |
| Source/Router ID    |       |
| Area ID             |       |
| Subnet/Net Mask     |       |
| Auth Type           |       |
|                     |       |
| Hello Interval      |       |
| Dead Interval       |       |
| Desig Router        |       |
| Backup Desig Router |       |


<br>
<br>

---
&nbsp;


### Link-State Routing Protocol
*What makes OSPF Link-State?* 

It builds a topology of the network.

<br>

~~~
!@R1
show ip ospf rib
~~~


<br>

__LSU__ - Link-State Updates  
__LSA__ - Link-State Advertisement  

<br>

~~~
ospf.lsa == 1  
ospf.lsa == 2  
ospf.lsa == 3  
~~~

<br>

- Type 1 LSA - (__O__) Router LSA : Router info
- Type 2 LSA - (__O__) Network LSA : via DR/BDR Network Routes
- Type 3 LSA - (__O IA__) Summary LSA
- Type 4 LSA - (__O E2__) Summary ASBR LSA
- Type 5 LSA - (__O E1 / E2__) AS-External LSA
- Type 6 LSA - OSPF Group Membership LSA
- Type 7 LSA - (__O N1 / N2__) NSSA LSA
- Type 8 LSA - OSPFv2 External Attributes & Link Local LSA OSPFv3

<br>

~~~
!@EDGE
conf t
 int lo#$34T#
  ip add #$34T#.#$34T#.#$34T#.#$34T# 255.255.255.255
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


<br>
<br>

---
&nbsp;


### OSPF States
D: __Down__ - The initial state where no hello packets have been received from a neighbor  

<br>

I: __Init__ - A hello packet has been received from a neighbor, but that neighbor's Router ID was not included in the hello packet, indicating a lack of bidirectional communication  

<br>

T: __Two-way__ - Bidirectional communication is established, as both routers have received each other's Router IDs in hello packets. DR/BDR Election occurs.  

<br>

E: __Exstart__ - Routers determine who will be the master and who will be the slave for the upcoming database exchange. The router with the higher Router ID becomes the master and begins the exchange of Database Description (DBD) packets, synchronizing sequence numbers.  

<br>

E: __Exchange__ - Routers exchange DBD packets to describe their Link State Databases (LSDBs). They compare the contents and identify any missing link-state information  

<br>

L: __Loading__ - Routers request the missing link-state information by sending Link-State Requests (LSRs). They then receive Link-State Updates (LSUs) and acknowledge them with Link-State Acknowledgements (LSAs)  

<br>

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


### Neighborship vs Adjacency
*Practice Doing the wrong things*

<br>

1. Mismatched Network Type
~~~
!@R2
conf t
 int e1/1
  ip ospf network point-to-point
  end
show ip ospf neighbor
clear ip ospf process
~~~

<br>

~~~
!@R1
show ip route ospf
~~~

<br>

__FIX__
~~~
!@R2
conf t
 int e1/1
  no ip ospf network point-to-point
  end
show ip ospf neighbor
clear ip ospf process
~~~


&nbsp;
---
&nbsp;


2. Mismatched Hello & Dead Timers
~~~
!@R2
conf t
 int e1/1
  ip ospf hello-interval 20
  end
show ip ospf neighbor
clear ip ospf process
~~~

<br>

__FIX__
~~~
!@R2
conf t
 int e1/1
  ip ospf hello-interval 10
  end
show ip ospf neighbor
~~~


&nbsp;
---
&nbsp;


3. Mismatch Authentication
~~~
!@R2
conf t
 int e1/1
  ip ospf authentication message-digest
  ip ospf message-digest-key 1 md5 C1sc0123
  end
show ip ospf neighbor
clear ip ospf process
~~~

<br>

__FIX__
~~~
!@R2
conf t
 int e1/1
  no ip ospf authentication message-digest
  no ip ospf message-digest-key 1 md5 C1sc0123
  end
show ip ospf neighbor
~~~


&nbsp;
---
&nbsp;


4. Mismatch Stub Flags
~~~
!@R2
conf t
 router ospf 1
  area 12 stub
  end
show ip ospf neighbor
clear ip ospf process
~~~

<br>

__FIX__
~~~
!@R2
conf t
 router ospf 1
  no area 12 stub
  end
show ip ospf neighbor
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


<br>
<br>

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
!@R4, C1, R3
show ip route
~~~


<br>
<br>

---
&nbsp;


## OSPF Metric Calculation  

$$
\text{Cost (Per eggress)} = \frac{\text{Reference Bandwidth}}{\text{Interface Bandwidth (mbps) }}
$$

<br>

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


### 🎯 Exercise 06: From R3, determine OSPF Cost to reach 10.1.1.0/30 and 1.1.1.1/32

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


## BGP

| Device    | ASN  |
| ---       | ---  |
| R1        | 1    |
| I1        | 34   |
| I2        | 25   |
| I3        | 34   |
| GoogleDNS | 25   |

<br>

~~~
!@R1
conf t
 router bgp 1
  bgp log-neighbor-changes
   neighbor 208.8.8.4 remote-as 34
   neighbor 207.7.7.2 remote-as 25
   neighbor 209.9.9.3 remote-as 34
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
 router bgp 34
  bgp log-neighbor-changes
  neighbor 24.2.4.2 remote-as 25
  neighbor 45.4.5.5 remote-as 25
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

~~~
!@I3 - GLOBE
conf t
 router bgp 34
  bgp log-neighbor-changes
  neighbor 32.3.2.2 remote-as 25
  neighbor 35.3.5.5 remote-as 25
  neighbor 209.9.9.1 remote-as 1
  address-family ipv4
   network 209.9.9.0 mask 255.255.255.0
   network 32.3.2.0 mask 255.255.255.0
   network 33.33.33.33 mask 255.255.255.255
   network 35.3.5.0 mask 255.255.255.0
   end
~~~

~~~
!@I4 - GOOGLE
config t
 router bgp 25
  bgp log-neighbor-changes
  neighbor 25.2.5.2 remote-as 25
  neighbor 35.3.5.3 remote-as 34
  neighbor 45.4.5.4 remote-as 34
  address-family ipv4
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


### 🎯 Exercise 07: Configure BGP on I2(PLDT). Set the ASN number to 25

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
  network __.__.__.__ mask __.__.__.__
  network __.__.__.__ mask __.__.__.__
  network __.__.__.__ mask __.__.__.__
  network __.__.__.__ mask __.__.__.__
  network __.__.__.__ mask __.__.__.__
  end
~~~


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


### BGP  ~~Hello~~ Messages  

~~~
!@C1
conf t
 int e3/3
  no shut
  no sw
  exit
 int e1/0
  no sw
  no shut
  ip add 100.0.0.1 255.255.255.0
  exit
 no router bgp 65531
 router bgp 65531
  bgp log-neighbor-changes
  neighbor 100.0.0.2 remote-as 65532
  address-family ipv4
   neighbor 100.0.0.2 activate
   network 100.0.0.0 mask 255.255.255.0
   !
 monitor session 1 source int e1/0 both
 monitor session 1 dest int e3/3
 end
~~~

~~~
!@S1
conf t
 int lo1
  ip add 100.100.100.100 255.255.255.255
  exit
 int e1/0
  no shut
  ip add 100.0.0.2 255.255.255.0
  exit
 no router bgp 65532
 router bgp 65532
  bgp log-neighbor-changes
  neighbor 100.0.0.1 remote-as 65531
  address-family ipv4
   neighbor 100.0.0.1 activate
   network 100.0.0.0 mask 255.255.255.0
   network 100.100.100.100 mask 255.255.255.255
   end
~~~


&nbsp;
---
&nbsp;


### 1. Notification - Indicate an error and terminate the BGP session.
~~~
!@S1
conf t
 router bgp 65532
  no neighbor 100.0.0.1 remote-as 65531
  end
~~~


&nbsp;
---
&nbsp;


### 2. Open Message - Establish a BGP session between two peers.
~~~
!@S1
conf t
 router bgp 65532
  neighbor 100.0.0.1 remote-as 65531
  end
~~~


&nbsp;
---
&nbsp;


### 3. __Keepalive__ - Maintain the BGP session alive without sending routing information.

Sent periodically if there's no UPDATE messages from its peer.
- Confirms that the session is still valid.
- Prevents the session from timing out.


&nbsp;
---
&nbsp;


### 4. __Update__ - Advertise or withdraw routes to a BGP peer.
*Advertised routes are contained within the NLRI (Network Layer Reachability Information)*

~~~
!@S1
conf t
 int lo1
  ip add 11.11.11.11 255.255.255.255
  exit
 router bgp 65532
  address-family ipv4
   network 11.11.11.11 mask 255.255.255.255
   end
~~~


<br>
<br>

__Remove BGP__
~~~
!@C1
conf t
 no router bgp 65531
 int e1/0
  switchport
  end
~~~

~~~
!@S1
conf t
 no router bgp 65532
 no int lo1
 int e1/0
  no ip add
  end
~~~


<br>
<br>

---
&nbsp;


### IBGP vs EBGP

1. __Next-Hop Route Advertisements__

In iBGP, by default, the next-hop IP of a route learned from one iBGP peer is not changed when advertised to another iBGP peer.

<br>

`Next-Hop-Self`
Forces the router to replace the next-hop IP of advertised routes with its own IP address.

~~~
!@I2 - PLDT
conf t
 router bgp 25
  neighbor 25.2.5.5 next-hop-self
  end
~~~


&nbsp;
---
&nbsp;


2. __Drop BGP Route Advertisement from the same AS_PATH__
Normally, BGP drops any route containing its own AS to prevent loops.

`AS-Override`
Modifies the AS_PATH so that the AS number is replaced when advertising a route back into the same AS.

<br>

`AllowAS-in`
Ignore the default behavior of BGP and allow BGP routes with the same AS-PATH to be learned.

<br>

__ALLOWAS-IN__
~~~
!@I3 - GLOBE
conf t
 router bgp 34
  neighbor 32.3.2.2 allowas-in
  end
~~~

~~~
!@I1 - CONVERGE
conf t
 router bgp 34
  neighbor 24.2.4.2 allowas-in
  end
~~~


<br>


__AS-OVERRIDE__
~~~
!@I4 - GOOGLE
conf t
 router bgp 25
  neighbor 35.3.5.3 as-override
  neighbor 45.4.5.4 as-override
  end
~~~


<br>
<br>

---
&nbsp;


### Candidate Default Route Propagation

~~~
!@R1
conf t
 router ospf 1
  default-information originate always
  end
~~~


<br>
<br>

---
&nbsp;


## NAT & PAT

~~~
!@R1
conf t
 access-list 1 permit 10.0.0.0 0.255.255.255
 access-list 1 permit 172.16.0.0 0.15.255.255
 access-list 1 permit 192.168.0.0 0.0.255.255
 int range e1/1-3
  ip nat outside
  exit
 int e1/0
  ip nat inside
  exit
 !
 ip nat inside source list 1 interface ethernet 1/1 overload
~~~

<br>

__Route Map__
~~~
!@R1
conf t
 access-list 1 permit 10.0.0.0 0.255.255.255
 access-list 1 permit 172.16.0.0 0.15.255.255
 access-list 1 permit 192.168.0.0 0.0.255.255
 !
 route-map PBR_CONVERGE permit 10
  match ip address 1
  match interface e1/1
 route-map PBR_PLDT permit 10
  match ip address 1
  match interface e1/2
 route-map PBR_GLOBE permit 10
  match ip address 1
  match interface e1/3
 !
 ip nat pool POOL7 207.7.7.10 207.7.7.254 netmask 255.255.255.0  
 ip nat pool POOL8 208.8.8.10 208.8.8.254 netmask 255.255.255.0
 ip nat pool POOL9 209.9.9.10 209.9.9.254 netmask 255.255.255.0
 !
 ip nat inside source route-map PBR_CONVERGE pool POOL8 overload
 ip nat inside source route-map PBR_PLDT pool POOL7 overload
 ip nat inside source route-map PBR_GLOBE pool POOL9 overload
 end
~~~


<br>
<br>

---
&nbsp;


## BGP ATTRIBUTES 

The BGP path attributes are the characteristics for all BGP advertised routes. Additionally to the necessary informations to perform basic routing , the path attributes allow BGP to set routing policies and advertise them. Each attribute is a member of one of the following categories:

1. __Well-known mandatory__ – This attribute has to be known and implemented by all BGP implementations

2. __Well-known discretionary__ – This attribute has to be known by all BGP implementations, but does not have to be sent in an update message.

3. __Optional transitive__ – This attribute does not have to be known by all BGP implementations but the BGP prozess has to accept the path within the attribute is found and forward it to other BGP peers, even though the BGP process doesnt know the attribute.

4. __Optional non-transitive__ – An update with an attribute from this category can be ignored. The router does not have to advertise this route nor the path to its peers.


<br>
<br>

~~~
!@R1
traceroute 8.8.8.8
show bgp
~~~


<br>
<br>


UPDATE contains the following:
- Weight
- LocPrf
- Self Originated
- AS Path
- Origin
- Metric
- Ex/Internal


<br>
<br>

1. Weight
2. Local Preference
3. Locally originated
4. AS Path length
5. Origin code
6. MED
7. eBGP over iBGP
8. Lowest IGP metric to the next hop (hot potato routing)
9. Oldest path
10. Lowest BGP Router ID
11. Lowest neighbor IP address


<br>
<br>

---
&nbsp;


## WEIGHT - Locally assigned
### 🎯 Exercise 08: Make R1 Prefer 208.8.8.4 as the next-hop
~~~
!@R1
conf t
 router bgp 1
  neighbor 208.8.8.4 weight 200
  end
clear ip bgp * soft
show bgp 8.8.8.8
sh bgp
~~~

<br>

~~~
!@R1
conf t
 router bgp 1
  no neighbor 208.8.8.4 weight 200
  end
clear ip bgp * soft
show bgp 8.8.8.8
sh bgp
~~~


&nbsp;
---
&nbsp;


### MANIPULATE BGP METRICS : ROUTE MAPS

__A.__ - Access List
__M.__ - Match
__S.__ - Set


~~~
!@GoogleDNS
config t
 interface Loopback1
  ip address 51.51.51.51 255.255.255.255
 interface Loopback2
  ip address 52.52.52.52 255.255.255.255
 interface Loopback3
  ip address 53.53.53.53 255.255.255.255
 interface Loopback4
  ip address 54.54.54.54 255.255.255.255
 router bgp 25
  network 51.51.51.51 mask 255.255.255.255
  network 52.52.52.52 mask 255.255.255.255
  network 53.53.53.53 mask 255.255.255.255
  network 54.54.54.54 mask 255.255.255.255
  end
~~~


<br>
<br>

---
&nbsp;


### 🎯 Exercise 09: Manipulate BGP Paths using Weight Attribute via Route Maps

- If we want to go to 51.51.51.51 we use ISP1:CONVERGE(208.8.8.4)
- If we want to go to 52.52.52.52 we use ISP2:PLDT(207.7.7.2)
- If we want to go to 53.53.53.53 we use ISP3:GLOBE(209.9.9.3)

<br>

~~~
!@R1
config t
 access-list 51 permit host 51.51.51.51
 access-list 53 permit host 53.53.53.53
 !
 route-map ISP1for51 permit 10
  match ip address 51
  set weight 51
 route-map ISP1for51 permit 20
  !
 route-map ISP3for53 permit 10
  match ip address 53
  set weight 53
 !
 route-map ISP3for53 permit 20
  !
 router bgp 1
  neighbor 208.8.8.4 route-map ISP1for51 in
  neighbor 209.9.9.3 route-map ISP3for53 in
  end
clear ip bgp * soft
~~~

<br>

~~~
!@R1
conf t
 router bgp 1
  no neighbor 208.8.8.4 route-map ISP1for51 in
  no neighbor 209.9.9.3 route-map ISP3for53 in
  end
clear ip bgp * soft
~~~


<br>
<br>

---
&nbsp;


### 🎯 Exercise 10: Manipulate BGP Paths using Weight Attribute via Route Maps

- If we want to go to 54.54.54.54 we use ISP1:CONVERGE(208.8.8.4)
- If we want to go to 55.55.55.55 we use ISP3:GLOBE(209.9.9.3)


~~~
!@R1
config t
 access-list
 !
 route-map 
  match 
  set 
 !
 router bgp 1
  neighbor 208.8.8.4
  neighbor 209.9.9.3
  end
clear ip bgp * soft
~~~


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


## LOCAL PREFERENCE 
- Keyword: Local
- Req: Must have same AS number
- NOTE: Local Pref >= 100: IDAAN MO SA AKIN
- NOTE: Local Pref < 100: WAG MO IDAAN SA AKIN
- Keyword sa Local Pref: AS Number


&nbsp;
---
&nbsp;


### 🎯 Exercise 11: Manipulate Local Pref for AS 25
- 51.51.51.51 local pref of 515
- 52.52.52.52 local pref of 525
- 53.53.53.53 local pref of 535  : BLOCK

<br>

~~~
!@GOOGLE-DNS
config t
 access-list 51 permit host 51.51.51.51
 access-list 52 permit host 52.52.52.52
 access-list 53 permit host 53.53.53.53
 !
 route-map LP1 permit 10
  match ip address 51
  set local-pref 515
 route-map LP1 permit 20
  match ip address 52
  set local-pref 525
 route-map LP1 Deny 30
  match ip address 53
  set local-pref 535
 route-map LP1 Permit 40
  !
 router bgp 25
  neighbor 25.2.5.2 route-map LP1 out
  end
clear ip bgp * soft
~~~


<br>
<br>

---
&nbsp;


### 🎯 Exercise 12: Manipulate Local Pref for AS 25
- 54.54.54.54 local pref of 545
- 55.55.55.55 local pref of 555
- 8.8.8.8     local pref of 888  : BLOCK



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


## AS-PATH
~~~
!@ISP1 - Converge
conf t
 route-map ASPATH1 permit 10
  set as-path prepend 34 34 34 34 34
  exit
 router bgp 34
  neighbor 208.8.8.1 route-map ASPATH1 OUT
  end
clear ip bgp * soft
~~~

<br>

~~~
!@ISP2 - PLDT
config t
 route-map ASPATH2 permit 10
  set as-path prepend 25 25 25 25 25
 !
 router bgp 25
  neighbor 207.7.7.1 route-map ASPATH2 OUT
  end
clear ip bgp * soft
~~~


<br>
<br>


Back to normal
~~~
!@ISP1 - Converge
conf t
 router bgp 34
  no neighbor 208.8.8.1 route-map ASPATH1 OUT
  end
clear ip bgp * soft
~~~

<br>

~~~
!@ISP2 - PLDT
config t
 router bgp 25
  no neighbor 207.7.7.1 route-map ASPATH2 OUT
  end
clear ip bgp * soft
~~~


<br>
<br>

---
&nbsp;


## MED - Multi Exit Discriminator
~~~
!@ISP2 - PLDT
config t
 access-list 2 permit host 55.55.55.55
 access-list 3 permit host 22.22.22.22
 no route-map MEDnotISP2
 route-map MEDnotISP2 permit 10
  match ip address 2 3
  set metric 69
  set as-path prepend 25 25
 route-map MEDnotISP2 permit 20
 !
 router bgp 25
  neigh 207.7.7.1 route-map MEDnotISP2 out
  end
clear ip bgp * soft
~~~


<br>
<br>

---
&nbsp;


## Network Optimization

### Passive Interface
~~~
!@A1
conf t
 router eigrp CCNPLEVEL
  address-family ipv4 unicast auto 100
   af-interface e0/0
    passive-interface
	end
~~~

<br>

~~~
!@A2,C1,C2
conf t
 router eigrp CCNPLEVEL
  address-family ipv4 unicast auto 100
   af-interface e1/0
    passive-interface
	end
~~~

<br>

~~~
!@R1
conf t
 router ospf 1
  passive-interface lo1
  end
~~~

<br>

~~~
!@R2
conf t
 router ospf 1
  passive-interface lo2
  end
~~~

<br>

~~~
!@R3
conf t
 router ospf 1
  passive-interface lo3
  end
~~~

<br>

~~~
!@R4
conf t
 router ospf 1
  passive-interface lo4
  end
~~~


&nbsp;
---
&nbsp;


### Route Summarization
~~~
!@R2
conf t
 int lo8
  ip add 10.10.8.1 255.255.255.0
  ip ospf 1 area 22
 int lo9
  ip add 10.10.9.1 255.255.255.0
  ip ospf 1 area 22
 int lo10
  ip add 10.10.10.1 255.255.255.0
  ip ospf 1 area 22
 int lo11
  ip add 10.10.11.1 255.255.255.0
  ip ospf 1 area 22
 int lo33
  ip add 10.10.33.1 255.255.255.128
  ip ospf 1 area 22
 int lo34
  ip add 10.10.33.129 255.255.255.128
  ip ospf 1 area 22
 int lo35
  ip add 10.10.34.1 255.255.255.128
  ip ospf 1 area 22
 int lo36
  ip add 10.10.34.129 255.255.255.128
  ip ospf 1 area 22
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


<br>

2. From the specified octet, find the difference between the first network (8) and the last (11).

<br>

3. Based on the difference (3), determine the next closes i.

<br>

4. Determine the new slash based on the chosen i (4i) and the octet (3rd) where the networks increments.


<br>

5. Finally, apply the new CIDR (/22) to the lowest network (10.10.8.0). Then, find the network.


<br>

~~~
!@R2
conf t
 router ospf 1
  area 22 range 10.10.8.0 255.255.252.0
  end
~~~


<br>
<br>

---
&nbsp;


### 🎯 Excercise 13: Summarize routes from loopback 33 - loopback 36
~~~
!@R2
conf t
 router ospf __
  area __ range __.__.__.__  __.__.__.__
  end
~~~

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


Remove All summarizations
~~~
!@R2
conf t
 router ospf 1
  no area 22 range 10.10.8.0 255.255.252.0
  no area 22 range 10.10.32.0 255.255.252.0
  end
~~~


<br>
<br>

---
&nbsp;


### 🎯 Excercise 14: Summarize both summarized routes

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


### Route Filtering
*Must be done on ABR or ASBR

Prefix List : `ip prefix-list [NAME] seq [10] [permit/deny] [x.x.x.x/x] [ge/le] [expected /mask]`

__ABR__
~~~
!@R2
conf t
 ip prefix-list NO-LOOP seq 10 deny 10.10.0.0/20 ge 32
 ip prefix-list NO-LOOP seq 20 deny 10.10.32.0/22 ge 32
 ip prefix-list NO-LOOP seq 30 permit 0.0.0.0/0 le 32   ! Subnet mask less than or equal to /32
 !
 router ospf 1
  area 0 filter-list prefix NO-LOOP in
  end
~~~


<br>
<br>

---
&nbsp;


# IPv6 Routing

## IPv6 BGP

~~~
!@ISP4 - GOOGLE
conf t
 router bgp 25
  neigh b:3:4:b::3 remote-as 34
  neigh b:2:4:b::2 remote-as 25
  neigh b:1:4:b::4 remote-as 34
  address-family ipv6
   neigh b:3:4:b::3 activate
   neigh b:2:4:b::2 activate
   neigh b:1:4:b::4 activate
   network b55::1/128
   network 8:8:8:8::8888/128
   network 2001:4860:4860::8844/128
   network b:3:4:b::/64
   network b:2:4:b::/64
   network b:1:4:b::/64
   end
~~~

<br>

~~~
!@ISP3 - GLOBE
conf t
 router bgp 34
  neigh b:3:4:b::5 remote-as 25
  neigh b:1:2:b::2 remote-as 25
  neigh b:1:33:b::1 remote-as 1
  address-family ipv6
   neigh b:3:4:b::5 activate
   neigh b:1:2:b::2 activate
   neigh b:1:33:b::1 activate
   network b:3:4:b::/64
   network b:1:2:b::/64
   network b:1:33:b::/64
   network b33::1/128
   end
~~~

<br>

~~~				
!@ISP2 - PLDT
conf t
router bgp 25
 neigh b:2:1:b::4 remote-as 34
 neigh b:2:4:b::5 remote-as 25
 neigh b:1:2:b::3 remote-as 34
 neigh b:1:22:b::1 remote-as 1
 address-family ipv6
  neigh b:2:4:b::5 activate
  neigh b:2:1:b::4 activate
  neigh b:1:2:b::3 activate
  neigh b:1:22:b::1 activate
  network b:1:2:b::/64
  network b:2:1:b::/64
  network b:1:22:b::/64
  network b22::1/128
  end
~~~

<br>

~~~
!@ISP1 - Converge
conf t
 router bgp 34
  neigh b:1:4:b::5 remote-as 25
  neigh b:2:1:b::2 remote-as 25
  neigh b:1:11:b::1 remote-as 1
  address-family ipv6
   neigh b:1:4:b::5 activate
   neigh b:2:1:b::2 activate
   neigh b:1:11:b::1 activate
   network b:1:4:b::/64
   network b:2:1:b::/64
   network b:1:11:b::/64
   network b44::1/128
   end
~~~

<br>

~~~
!@R1
conf t
 router bgp 1
  neigh b:1:33:b::3 remote-as 34
  neigh b:1:22:b::2 remote-as 25
  neigh b:1:11:b::4 remote-as 34
  address-family ipv6
   neigh b:1:33:b::3 activate
   neigh b:1:22:b::2 activate
   neigh b:1:11:b::4 activate
   network FEC0:1::/122
   network b:1:33:b::/64
   network b:1:22:b::/64
   network b:1:11:b::/64
   end
~~~


<br>
<br>


__AS-OVERRIDE/ALLOWAS-IN__


<br>
<br>

---
&nbsp;


## Tunnel v6 to v4

~~~
!@R3
conf t
 interface Tunnel34
  no ip address
  ipv6 address 2026::34:1/122
  tunnel source lo3
  tunnel destination 4.4.4.4
  tunnel mode ipv6ip
  end
~~~

<br>

~~~
!@R4
conf t
 interface Tunnel34
  no ip address
  ipv6 address 2026::34:2/122
  tunnel source lo4
  tunnel destination 3.3.3.3
  tunnel mode ipv6ip
 end
~~~


&nbsp;
---
&nbsp;


## OSPFv3

~~~
!@R1
conf t
 ipv6 router ospf 6
  router-id 1.1.1.1
 int lo1
  ipv6 ospf 6 area 12
 int e1/0
  ipv6 ospf 6 area 12
  end
~~~

<br>

~~~
!@R2
conf t
 ipv6 router ospf 6
  router-id 2.2.2.2
 int lo2
  ipv6 ospf 6 area 0
 int e1/1
  ipv6 ospf 6 area 0
 int e1/2
  ipv6 ospf 6 area 12
  end
~~~

<br>

~~~
!@R3
conf t
 ipv6 router ospf 6
  router-id 3.3.3.3
 int lo3
  ipv6 ospf 6 area 0
 interface Tunnel34
  ipv6 ospf 6 area 34
 int e1/1
  ipv6 ospf 6 area 0
  end
~~~

<br>

~~~
!@R4
conf t
 ipv6 router ospf 6
  router-id 4.4.4.4
 int lo4
  ipv6 ospf 6 area 34
 interface Tunnel34
  ipv6 ospf 6 area 34
  end
~~~


<br>
<br>

---
&nbsp;


### OSPFv6 & BGP Redistribution
~~~
!@R1
config t
 ipv6 router ospf 6
  default-information originate always
  redistribute bgp 1 metric 69
 router bgp 1
  address-family ipv6 unicast
   redistribute ospf 6 match internal external 1 external 2 include-connected
   end
~~~


<br>
<br>

---
&nbsp;


## EIGRP IPv6

~~~
!@R4
conf t
 ipv6 router eigrp 10
  eigrp router-id 4.4.4.4
  no shut
 int e1/0
  ipv6 eigrp 10
 int e1/1
  ipv6 eigrp 10
  end
~~~

<br>

~~~
!@C1
conf t
 ipv6 router eigrp 10
  eigrp router-id 10.2.1.1
  no shut
 int lo1
  ipv6 eigrp 10
 int e1/1
  ipv6 eigrp 10
 int vlan 10
  ipv6 eigrp 10
 int vlan 20
  ipv6 eigrp 10
 int vlan 100
  ipv6 eigrp 10
  end
~~~

<br>

~~~	
!@C2
conf t
 ipv6 router eigrp 10
  eigrp router-id 10.2.1.2
  no shut
 int lo1
  ipv6 eigrp 10
 int e1/1
  ipv6 eigrp 10
 int vlan 10
  ipv6 eigrp 10
 int vlan 20
  ipv6 eigrp 10
 int vlan 200
  ipv6 eigrp 10
  end
~~~

<br>


## EIGRP IPv6 & OSPFv3 Redistribution

~~~
!@R4
conf t
 ipv6 router ospf 6
  redistribute eigrp 10 include-connected 
 ipv6 router eigrp 10
  redistribute ospf 6 metric 10000 100 255 1 1500 include-connected
  end
~~~


<br>
<br>

---
&nbsp;


## IPv6 Address Management
- DHCPv4 & DHCPv6
- Autoconfig
- EUI-64

<br>

~~~
!@A1
conf t
 int e0/0
  switchport mode access
  switchport access vlan 10
  end
~~~

<br>

~~~
!@A2
conf t
 int e1/0
  switchport mode access
  switchport access vlan 10
  end
~~~

<br>

~~~
!@C1
conf t
 vlan 10
  no remote-span
 no monitor session 1
 !
 ip dhcp excluded-address 10.2.1.1 10.2.1.100
 ip dhcp pool CCNPv4
  network 10.2.1.0 255.255.255.0
  default-router 10.2.1.1
  domain-name CCNPv4.COM
  dns-server 10.2.1.1
 !
 ipv6 unicast-routing
 !
 ipv6 dhcp pool CCNPv6
  address prefix 10:2:1:12::0/64
  domain-name CCNPv6.COM
  exit
 !
 int vlan 10
  no shut
  ipv6 address 10:2:1:12::1/64
  ipv6 dhcp server CCNPv6
  ipv6 nd managed-config-flag
  ipv6 nd other-config-flag
  end
sh ipv6 dhcp pool 
~~~

<br>

~~~
!@P1
conf t
 ipv6 unicast-routing
 int e0/0
  ipv6 add 10:2:1:12::B00B/64
end


conf t
 no ipv6 unicast-routing
 int e0/0
  ipv6 add dhcp
  ip add dhcp
  end
~~~

<br>

~~~
!@P2
config t
 ipv6 unicast-routing
 ipv6 route ::/0 10:2:1:12::2
 int e1/0
  ip add dhcp
  ipv6 address 10:2:1:12::/64 eui-64
  no shut
  end
~~~
