# Wireshark Example 1

> Almost get ready for wireshark

## Commands

```
git clone https://github.com/mbigras/wireshark_example1
cd wireshark_example1
vagrant up
ansible all -m ping
ansible-playbook playbooks/example1.yml
```

## aci

```
vagrant ssh aci
sudo su - alice
```

```
sudo /usr/sbin/tcpdump -i eth1
```

```
echo hello world | nc -l 3000
```

## bop

```
vagrant ssh bop
sudo su - bob
```

```
sudo /usr/sbin/tcpdump -i eth1
```

```
curl aci:3000
```

## Clean up

```
vagrant destroy -f
```

## Output

```
alice@aci:~$ sudo /usr/sbin/tcpdump -i eth1
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eth1, link-type EN10MB (Ethernet), capture size 262144 bytes
04:37:22.050823 IP aci.58946 > bop.3000: Flags [S], seq 4126711063, win 29200, options [mss 1460,sackOK,TS val 716050 ecr 0,nop,wscale 7], length 0
04:37:22.051269 IP bop.3000 > aci.58946: Flags [S.], seq 1515009425, ack 4126711064, win 28960, options [mss 1460,sackOK,TS val 706303 ecr 716050,nop,wscale 7], length 0
04:37:22.051289 IP aci.58946 > bop.3000: Flags [.], ack 1, win 229, options [nop,nop,TS val 716050 ecr 706303], length 0
04:37:22.051390 IP aci.58946 > bop.3000: Flags [P.], seq 1:73, ack 1, win 229, options [nop,nop,TS val 716050 ecr 706303], length 72
04:37:22.051497 IP bop.3000 > aci.58946: Flags [.], ack 73, win 227, options [nop,nop,TS val 706303 ecr 716050], length 0
04:37:22.051766 IP bop.3000 > aci.58946: Flags [P.], seq 1:13, ack 73, win 227, options [nop,nop,TS val 706303 ecr 716050], length 12
04:37:22.051773 IP aci.58946 > bop.3000: Flags [.], ack 13, win 229, options [nop,nop,TS val 716050 ecr 706303], length 0
04:37:23.555441 IP 192.168.33.1.17500 > 192.168.33.255.17500: UDP, length 169
04:37:27.061447 ARP, Request who-has aci tell bop, length 46
04:37:27.061477 ARP, Reply aci is-at 08:00:27:50:9c:46 (oui Unknown), length 28
04:37:53.616083 IP 192.168.33.1.17500 > 192.168.33.255.17500: UDP, length 169
```

```
bob@bop:~$ sudo /usr/sbin/tcpdump -i eth1
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eth1, link-type EN10MB (Ethernet), capture size 262144 bytes
04:37:22.040095 IP aci.58946 > bop.3000: Flags [S], seq 4126711063, win 29200, options [mss 1460,sackOK,TS val 716050 ecr 0,nop,wscale 7], length 0
04:37:22.040188 IP bop.3000 > aci.58946: Flags [S.], seq 1515009425, ack 4126711064, win 28960, options [mss 1460,sackOK,TS val 706303 ecr 716050,nop,wscale 7], length 0
04:37:22.040492 IP aci.58946 > bop.3000: Flags [.], ack 1, win 229, options [nop,nop,TS val 716050 ecr 706303], length 0
04:37:22.040518 IP aci.58946 > bop.3000: Flags [P.], seq 1:73, ack 1, win 229, options [nop,nop,TS val 716050 ecr 706303], length 72
04:37:22.040526 IP bop.3000 > aci.58946: Flags [.], ack 73, win 227, options [nop,nop,TS val 706303 ecr 716050], length 0
04:37:22.040675 IP bop.3000 > aci.58946: Flags [P.], seq 1:13, ack 73, win 227, options [nop,nop,TS val 706303 ecr 716050], length 12
04:37:22.040755 IP bop.3000 > aci.58946: Flags [F.], seq 13, ack 73, win 227, options [nop,nop,TS val 706303 ecr 716050], length 0
04:37:23.545272 IP 192.168.33.1.17500 > 192.168.33.255.17500: UDP, length 169
04:37:27.052771 ARP, Request who-has aci tell bop, length 28
04:37:27.053263 ARP, Reply aci is-at 08:00:27:50:9c:46 (oui Unknown), length 46
04:37:53.621082 IP 192.168.33.1.17500 > 192.168.33.255.17500: UDP, length 169
04:37:59.214187 IP 192.168.33.1.mdns > 224.0.0.251.mdns: 0 [1a] [4q] PTR (QU)? _afpovertcp._tcp.local. PTR (QU)? _smb._tcp.local. PTR (QU)? _rfb._tcp.local. PTR (QU)? _adisk._tcp.local. (94)
04:38:00.219096 IP 192.168.33.1.mdns > 224.0.0.251.mdns: 0 [1a] [4q] PTR (QM)? _afpovertcp._tcp.local. PTR (QM)? _smb._tcp.local. PTR (QM)? _rfb._tcp.local. PTR (QM)? _adisk._tcp.local. (94)
```