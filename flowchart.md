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

```sequence
10.192.72.132 ->> ns01.hessoadm.ch: étape 1
ns01.hessoadm.ch->>racine '.': étape 2
racine '.' -->> ns01.hessoadm.ch:
ns01.hessoadm.ch->>'.com': étape 3
'.com' -->> ns01.hessoadm.ch:
ns01.hessoadm.ch->>'.gmail': étape 4
'.gmail' -->> ns01.hessoadm.ch:
ns01.hessoadm.ch->>'smtp': étape 5
'smtp' -->> ns01.hessoadm.ch:
ns01.hessoadm.ch -->> 10.192.72.132 :étape 6
```

```sequence
10.192.72.132 ->> ns01.hessoadm.ch: Standard query A smtp.gmail.com
ns01.hessoadm.ch->>10.192.72.132: Standard query response A smtp.gmail.com CNAME 
```

```sequence
10.192.72.132 ->> ns01.heig−vd.ch: étape 1
ns01.heig−vd.ch->>f.root−servers.net \n'.org': étape 2
f.root−servers.net \n'.org' -->> ns01.heig−vd.ch:
ns01.heig−vd.ch->>c0.org.afilias−nst.info\n'wikipedia.org.': étape 3
c0.org.afilias−nst.info\n'wikipedia.org.' -->> ns01.heig−vd.ch:
ns01.heig−vd.ch->>ns0.wikimedia.org\nfr.wikipedia.org.:étape 4
ns0.wikimedia.org\nfr.wikipedia.org.-->>ns01.heig−vd.ch:
ns01.heig−vd.ch -->> 10.192.72.132: étape 5
```

