````sequence
Vmware_26꞉7e꞉73->>Vmware_2c꞉70꞉d6: Who has 10.192.74.100 \n 1.65 ms [ARP]
Vmware_2c꞉70꞉d6->>Vmware_26꞉7e꞉73: 10.192.74.100 is at 00:50:56:2c:70:d6 \n 1.65 ms [ARP]
Vmware_2c꞉70꞉d6->>Vmware_26꞉7e꞉73: Who has 10.192.74.58 \n 6.79 ms [ARP]
Vmware_26꞉7e꞉73->>Vmware_2c꞉70꞉d6: 10.192.74.58 is at 00:50:56:26:7e:73 \n 6.79 ms [ARP]

````

```sequence
10.192.74.58->>10.192.74.100:echo(ping)request \n 1.65ms [ICMP]
10.192.74.100->>10.192.74.58:echo(ping)reply \n 1.65 ms [ICMP]
```

  ````sequence
Vmware_26꞉7e꞉73->>Cisco_ff꞉fc꞉3c: Who has 10.192.74.1
Cisco_ff꞉fc꞉3c->>Vmware_26꞉7e꞉73: 10.192.74.100 is at 00:08:e3:ff:fc:3c

  ````

````sequence
10.192.74.58->>8.8.8.8:echo(ping)request
8.8.8.8->>10.192.74.58:echo(ping)reply
````





