
<!-- Your monitor number = #$34T# -->


## ⛅ Warm Up for Day 3.
*"Repetition is the mother of all skills"*

<br>

### 🔧 Configure the following:
  - Switch (__CoreTAAS__ & __CoreBABA__)
  - Voice Gateway/Call Manager (__CUCM - Cisco Unified Call Manager__)
  - Router (__EDGE__)

<br>

Verify:

~~~cmd
@cmd
ping 10.#$34T#.1.10             PC Network Adapter
ping 10.#$34T#.1.2		    CoreTAAS
ping 10.#$34T#.1.4		    CoreBABA
ping 10.#$34T#.100.8		CUCM
ping 10.#$34T#.#$34T#.1		EDGE - INSIDE
ping 200.0.0.#$34T#		    EDGE - OUTSIDE

ping 200.0.0.k		        Klassmate's EDGE	       k = klassmate's Monitor Number
ping 10.k.100.8		        Klassmate's CUCM
ping 10.k.1.4		        Klassmate's CoreBABA
ping 10.k.1.2		        Klassmate's CoreTAAS
ping 10.k.1.10		        Klassmate's PC
~~~

Your Branch must be able to call other klassmates  

<br>

View your cameras:
  - http://10.#$34T#.50.6
  - http://10.#$34T#.50.8


<br>
<br>

---
&nbsp;


# 💻 Network Fundamentals

<br>

### 🔢 Counting as a network engineer.

|     | Decimal | IPv4          | IPv6   |
| --- | ---     | ---           | ---    |
| -1  | 1999    | 1.255.255.255 | :1fff: |
|     | 2000    | 2.0.0.0       | :2000: |
| +1  | 2001    | 2.0.0.1       | :2001: |
|     |         |               |        |
| -1  |         |               |        |
|     | 2999    | 2.255.255.255 | :2fff: |
| +1  |         |               |        |
|     |         |               |        |
| -1  |         |               |        |
|     | 4099    | 4.0.255.255   | :40ff: |
| +1  |         |               |        |
|     |         |               |        |
| -1  |         |               |        |
|     | 6790    | 6.7.255.0     | :67f0: |
| +1  |         |               |        |
|     |         |               |        |
| -1  |         |               |        |
|     | 5389    | 5.3.8.255     | :538f: |
| +1  |         |               |        |
|     |         |               |        |


&nbsp;
---
&nbsp;


### Internet Protocol Version 4 (IPv4)
*What is the IP address of your phone?*
  - ipchicken.com
  - ipconfig

<br>

### Public IP address
| Class | IP Range                    |
| ---   | ---                         |
| A     | 1.0.0.0 - 126.255.255.255   |
| B     | 128.0.0.0 - 191.255.0.0     |
| C     | 192.0.0.0 - 223.255.255.0   |
| D     | 224.0.0.0 - 239.255.255.255 |
| E     | 240.0.0.0 - 255.255.255.255 |

<br>

~~~cmd
@cmd
ping 8.8.8.8
ping 1.1.1.1
ping 4.4.1.1

tracert 8.8.8.8
~~~

<br>
<br>

<details>
<summary>Traceroute Output</summary>
	
~~~cmd
Tracing route to dns.google [8.8.8.8]
over a maximum of 30 hops:

  1    20 ms     1 ms     1 ms  10.28.0.1
  2     2 ms     1 ms     1 ms  192.168.100.1
  3    10 ms    10 ms     8 ms  10.56.0.1
  4     *        9 ms     *     161.49.4.128.convergeict.com [161.49.4.128]
  5     6 ms     4 ms     4 ms  161.49.4.240.convergeict.com [161.49.4.240]
  6     *        *        *     Request timed out.
  7     4 ms     5 ms     5 ms  161.49.6.147.convergeict.com [161.49.6.147]
  8     5 ms     5 ms     4 ms  142.250.174.148
  9     9 ms     5 ms     5 ms  142.251.251.137
 10     5 ms     5 ms     6 ms  142.251.246.167
 11     5 ms     9 ms     4 ms  dns.google [8.8.8.8]
~~~

</details>


&nbsp;
---
&nbsp;


### Private IP address  
*Why do big companies uses the IP addresses that starts with 10.x.x.x ? *

<br>

| Class | IP Range                        | No. of Host |
| ---   | ---                             | ---         |
| A     | 10.0.0.0 - 10.255.255.255       | 16,777,214  |
| B     | 172.16.0.0 - 172.31.255.255     | 64,534      |
| C     | 192.168.0.0 - 192.168.255.255   | 254         |


<br>
<br>
<br>
<br>

---
&nbsp;


## 🙌 CIDR (Rivan Finger Method)
*How do devices see IP addresses? *
	
### `0 0 0 0   0 0 0 0   .   0 0 0 0   0 0 0 0   .   0 0 0 0   0 0 0 0   .   0 0 0 0   0 0 0 0`

<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>


<br>
<br>

__Example 01:__
<details>
<summary>192.168.20.1 /24</summary>
	
### `1 1 0 0   0 0 0 0   .   1 0 1 0   1 0 0 0   .   0 0 0 1   0 1 0 0   .   0 0 0 0   0 0 0 1`

### `1 1 1 1   1 1 1 1   .   1 1 1 1   1 1 1 1   .   1 1 1 1   1 1 1 1   .   0 0 0 0   0 0 0 0`

<br>
<br>
<br>

### `1 1 0 0   0 0 0 0   .   1 0 1 0   1 0 0 0   .   0 0 0 1   0 1 0 0   .   1 1 1 1   1 1 1 1`

</details>

<br>

__Example 02:__
<details>
<summary>172.16.40.1 /21</summary>
	
### `1 0 1 0   1 1 0 0   .   0 0 0 1   0 0 0 0   .   0 0 1 0   1 0 0 0   .   0 0 0 0   0 0 0 1`

### `1 1 1 1   1 1 1 1   .   1 1 1 1   1 1 1 1   .   1 1 1 1   1 0 0 0   .   0 0 0 0   0 0 0 0`

<br>
<br>
<br>

### `1 0 1 0   1 1 0 0   .   0 0 0 1   0 0 0 0   .   0 0 1 0   1 1 1 1   .   1 1 1 1   1 1 1 1`

</details>

<br>

__Example 03:__
<details>
<summary>10.100.22.205 /30</summary>
	
### `0 0 0 0   1 0 1 0   .   0 1 1 0   0 1 0 0   .   0 0 0 1   0 1 1 0   .   1 1 0 0   1 1 0 1`

### `1 1 1 1   1 1 1 1   .   1 1 1 1   1 1 1 1   .   1 1 1 1   1 1 1 1   .   1 1 1 1   1 1 0 0`

<br>
<br>
<br>

### `0 0 0 0   1 0 1 0   .   0 1 1 0   0 1 0 0   .   0 0 0 1   0 1 1 0   .   1 1 0 0   1 1 1 1`

</details>


&nbsp;
---
&nbsp;


| Binary             | Decimal|
| ---                | ---    |
| `0 0 0 0  0 0 0 0` | = 0    |
| `0 0 0 0  0 0 0 1` | = 1    |
| `0 0 0 0  0 0 1 0` | = 2    |
| `0 0 0 0  0 0 1 1` | = 3    |
| `0 0 0 0  0 1 0 0` | = 4    |
| `0 0 0 0  0 1 0 1` | = 5    |
| `0 0 0 0  0 1 1 0` | = 6    |
| `0 0 0 0  0 1 1 1` | = 7    |
| `0 0 0 0  1 0 0 0` | = 8    |
| `0 0 0 0  1 0 0 1` | = 9    |
| `0 0 0 0  1 0 1 0` | = 10   |
| `0 0 0 0  1 0 1 1` | = 11   |
| `0 0 0 0  1 1 0 0` | = 12   |
| `0 0 0 0  1 1 0 1` | = 13   |
| `0 0 0 0  1 1 1 0` | = 14   |
| `0 0 0 0  1 1 1 1` | = 15   |
|                    |        |
| `0 0 0 1  0 0 0 0` | = 16   |


<br>
<br>

---
&nbsp;


### 🎯 Exercise 01: Convert CIDR to various formats

<br>

| CIDR | NETMASK     | RIVAN Format | WILDCARD    |
| ---  | ---         | ---          | ---         |
| /20  |             | (Octet, i)   |             |
| /27  |             | (Octet, i)   |             |
| /14  |             | (Octet, i)   |             |


<br>
<br>

---
&nbsp;


## 0️⃣ Bit Length

&nbsp;
---
&nbsp;

  
### 🎯 Exercise 02: Find the Bit Length

<br>

| Value     | Bits |
| ---       | ---  |
| 195       |      |
| 13        |      |
| 1,750     |      |
| 1,855     |      |
| 2,700     |      |
| 2         |      |
| 376       |      |
| 888       |      |
| 8         |      |
| 212       |      |
| 4,500     |      |
| 81        |      |
| 20,000    |      |
| 55        |      |
| your age  |      |


<br>
<br>

---
&nbsp;


##  Subnetting (Host)

### 🎯 Exercise 03: Design a network for `accenture.com` with 1750 agents, team leads, project managers, and quality assurance teams. Use the 10.0.0.0/8 IP address space. The first network is unavailable.
- [ ] 10.16.0.0/24
- [ ] 10.0.4.0/22
- [ ] 10.0.8.0/21
- [ ] 10.0.32.0/20

<br>
<br>

### CSI Method  
__CONVERT__  


<br>

__SUBTRACT__  


<br>

<details>
<summary>Why /32? </summary>

### `0 0 0 0  0 0 0 0  .  0 0 0 0  0 0 0 0  .  0 0 0 0  0 0 0 0  .  0 0 0 0  0 0 0 0`
### `                                                     0 0 0     0 0 0 0  0 0 0 0`
### `_______________________________________________________________________________`
### `0 0 0 0  0 0 0 0  .  0 0 0 0  0 0 0 0  .  0 0 0 0  0                           `

</details>

<br>
	
__INSERT (*IPASOK*)__  
(Octet, i)


<br>
<br>

---
&nbsp;


### 🎯 Exercise 04: Design a network for `concentrix.com` with 160 admin, 250 managers, 112 executive, 100 security agents. Use the 172.16.0.0/16 IP address space. The first network is unavailable.
- [ ] 172.16.8.0 /22
- [ ] 172.16.16.0 /23
- [ ] 172.16.4.0 /22
- [ ] 172.16.2.0 /23

<br>

CIA Method
- CONVERT:	
- SUBTRACT:
- INSERT(Ipasok):

<br>

|                               |                        |
| ---                           | ---                    |
| Network IP                    |                        |
| First Valid (Network +1)      |                        |
| Last Valid (Broadcast -1)     |                        |
| Broadcast (Next Network -1)   |                        |
|                               |                        |
| Next Network (Insert i again) |                        |


<br>
<br>

---
&nbsp;


### 🎯 Exercise 05: Design and implement a network for `foundever.com` with 45 users. Use the 192.168.0.0/24 IP address space
CIA Method
- CONVERT:	
- SUBTRACT:
- INSERT(Ipasok):

<br>

|                               |                        |
| ---                           | ---                    |
| Network IP                    |                        |
| First Valid (Network +1)      |                        |
| Last Valid (Broadcast -1)     |                        |
| Broadcast (Next Network -1)   |                        |
|                               |                        |
| Next Network (Insert i again) |                        |

<br>
<br>

__IMPLEMENTATION__

~~~
config t
 vlan 25
  name _____.com
  exit
 int vlan 25
  ip add __.__.__.__  __.__.__.__
  ip ospf 1 area 0
  no shut
  exit
 ip dhcp excluded-add __.__.__.__  __.__.__.__
 ip dhcp pool _____.com
  network __.__.__.__  __.__.__.__
  default-router __.__.__.__
  domain-name _____.com
  dns-server 10.#$34T#.1.10
  option 150 ip 10.#$34T#.100.8
 int fa 0/5
  switchport voice vlan 25
  shut
  no shut
  end
show ip dhcp binding
~~~


<br>
<br>

---
&nbsp;


### 🎯 Exercise 06: Design and implement networks.

<br>

P1
- IP address: 10.35.0.0/16
- Domain Name: BSP.COM
- Number of Users: 812
- Reserved IPs: First 70 IPs
- Assign to VLAN: 35

<br>

P1
- IP address: 172.16.64.0/18
- Domain Name: ACCENTURE.COM
- Number of Users: 87
- Reserved IPs: First 10 IPs
- Assign to VLAN: 40

<br>

S1
- IP address: 192.168.52.0/24
- Domain Name: TELETECH.NET
- Number of Users: 345
- Reserved IPs: First 100 IPs
- Assign to VLAN: 52
	
<br>

S2
- IP address: 10.67.48.0/20
- Domain Name: FOUNDEVER.COM
- Number of Users: 1456
- Reserved IPs: First 100 IPs
- Assign to VLAN: 67


<br>
<br>

---
&nbsp;


## VLSM (Variable Length Subnet Mask)

### 🎯 Exercise: Design a network for TELEPORFORMANCE.COM with the ff:
- ADMIN Dept: 14  Hosts
- FIN   Dept: 39  Hosts
- IT    Dept: 6   Hosts
- GUESTS    : 300 Hosts

Use the available IP address space: 10.21.80.0/20  

<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
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


### 🎯 Exercise: Design a network for BCLO.COM with the ff:
- ADMIN Dept: 123  Hosts
- FIN   Dept: 69  Hosts
- GUESTS    : 1800 Hosts

Use the available IP address space: 10.40.0.0/16

<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
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


## Finding the Network
TELNET Port 23   
: 10.#$34T#.1.4  
: 10.#$34T#.1.2  

<br>
<br>

<br>
<br>

---
&nbsp;


### 🎯 Exercise: Find the Network of the FF:

1. 10.15.201.72   /27
2. 192.168.115.15 /21
3. 172.16.1.214   /25
4. 192.168.55.137 /22


<br>
<br>

---
&nbsp;


## Static Routing
__Setup RSTHaypu Labs__


<br>
<br>

---
&nbsp;


### 🎯 Exercise: Configure a Static HOST Route from R1 to reach 10.1.1.5

<br>
<br>
<br>
<br>
<br>
<br>
<br>
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


### 🎯 Exercise: Configure a Static HOST Route from R4 to reach 10.1.2.9

<br>
<br>
<br>
<br>
<br>
<br>
<br>
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


### 🎯 Exercise: Configure a Static HOST Route from R1 to reach 10.1.1.6

<br>
<br>
<br>
<br>
<br>
<br>
<br>
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


### 🎯 Exercise: Configure a Static HOST Route from R1 to reach 10.1.1.10 (R4)

<br>
<br>
<br>
<br>
<br>
<br>
<br>
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


## Subnetting (Subnet)

<br>
<br>


### 🎯 Exercise 07: Subnet for 8 offices using the Network address 192.168.128.0/27  Maximize the number of IP addresses.

<br>

### CAI Method  
__CONVERT *(Bit Value. NOT Length)*__  


<br>

__ADD__  


<br>

__INSERT(*IPASOK*)__  


<br>

From the NETWORK:
Valid Range:  
- FIRST VALID:
- LAST VALID: 
- LAST IP/BROADCAST:

<br>

NEXT NETWORK:


<br>
<br>

---
&nbsp;


### 🎯 Exercise 08: Subnet for 16 offices using the Network address 172.16.224.0/19. Maximize the number of IP addresses.

CAI Method
- CONVERT:	
- ADD:
- INSERT(Ipasok):

<br>

Offices:
1. &nbsp;
2. &nbsp;
3. &nbsp;
4. &nbsp;
5. &nbsp;
6. &nbsp;
7. &nbsp;
8. &nbsp;
9. &nbsp;
10. &nbsp;
11. &nbsp;
12. &nbsp;
13. &nbsp;
14. &nbsp;
15. &nbsp;
16. &nbsp;
17. &nbsp;
18. &nbsp;
19. &nbsp;
20. &nbsp;


<br>
<br>

---
&nbsp;


### 🎯 Exercise 09: Design and Implement 4 offices using the Network address 172.16.32.0/19. Maximize the number of IP addresses.

CAI Method
- CONVERT:	
- ADD:
- INSERT(Ipasok):

<br>

Offices:
1. &nbsp;
2. &nbsp;
3. &nbsp;
4. &nbsp;




