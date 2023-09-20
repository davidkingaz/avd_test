# switch2 Commands Output

## Table of Contents

- [show lldp neighbors](#show-lldp-neighbors)
- [show ip interface brief](#show-ip-interface-brief)
- [show interfaces description](#show-interfaces-description)
- [show version](#show-version)
- [show running-config](#show-running-config)
## show interfaces description

```
Interface                      Status         Protocol           Description
Et1                            up             up                 
Et2                            up             up                 
Et3                            admin down     down               
Ma1                            up             up
```
## show ip interface brief

```
Address
Interface         IP Address             Status           Protocol           MTU    Owner  
----------------- ---------------------- ---------------- -------------- ---------- -------
Ethernet1         192.168.5.111/23       up               up                1500           
Ethernet3         172.25.10.2/24         admin down       down              1500           
Management1       unassigned             up               up                1500
```
## show lldp neighbors

```
Last table change time   : never
Number of table inserts  : 0
Number of table deletes  : 0
Number of table drops    : 0
Number of table age-outs : 0

Port          Neighbor Device ID       Neighbor Port ID    TTL
---------- ------------------------ ---------------------- ---
```
## show running-config

```
! Command: show running-config
! device: AristaSwitch (vEOS-lab, EOS-4.30.2F)
!
! boot system flash:/vEOS-lab.swi
!
no aaa root
!
username ansible privilege 15 secret sha512 $6$RvCYdz6zhW5Y2p92$aF1anCcLmr5Yxr2WXQ.BOjLfwfhPbATBWnXSfkyplyzxVBnLSstwDTdsIgiLOEYpowQvaR.LHx.QOTLirvFLl.
username arista privilege 15 secret sha512 $6$7InD1b5jdB2ic/KO$EOEmwHcZIC7BULcM6P3hJl2H1A4QcimBB6hzL2360wYToN.NtVAwblcnPtRMtcO/Ygx8Fz6ffRuBqyxVYLlQV.
!
transceiver qsfp default-mode 4x10G
!
service routing protocols model multi-agent
!
hostname AristaSwitch
ip name-server vrf default 192.168.5.77
ip name-server vrf default 192.168.5.83
!
snmp-server community READ ro
snmp-server community WRITE rw
!
spanning-tree mode mstp
!
system l1
   unsupported speed action error
   unsupported error-correction action error
!
vlan 10
!
management api http-commands
   no shutdown
!
interface Ethernet1
   no switchport
   ip address 192.168.5.111/23
!
interface Ethernet2
   switchport access vlan 10
!
interface Ethernet3
   shutdown
   no switchport
   ip address 172.25.10.2/24
   ip ospf area 0.0.0.10
!
interface Management1
!
ip routing
!
ip route 0.0.0.0/0 192.168.4.1
!
ntp server 8.8.8.8
!
router ospf 1
   router-id 2.2.2.2
   network 172.18.0.0/16 area 0.0.0.20
   network 172.25.0.0/16 area 0.0.0.10
   network 192.168.0.0/16 area 0.0.0.0
   max-lsa 12000
!
ip ospf router-id output-format hostnames
!
end
```
## show version

```
Arista vEOS-lab
Hardware version: 
Serial number: AF12C3928ADAE3CBBBDB9D2A365FB1CB
Hardware MAC address: 5254.002a.40b0
System MAC address: 5254.002a.40b0

Software image version: 4.30.2F
Architecture: i686
Internal build version: 4.30.2F-33092737.4302F
Internal build ID: 90401380-ca95-4956-a605-ecece601c8f9
Image format version: 1.0
Image optimization: None

Uptime: 1 week, 0 days, 23 hours and 9 minutes
Total memory: 1988144 kB
Free memory: 980716 kB
```
