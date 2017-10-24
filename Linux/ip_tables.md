# IP Tables

### Common Commands

|Function|Command
|--------|--------|
|Dump w/ counters|`iptables-save -c <file`|
|Restore|`iptables-restore <file`|
|List all IP tables|`iptables -L -v --line-numbers`|
|Flush all rules|`iptables -F`|
|Drop all Packets|`iptables -P IPUT DROP`|
|Turn off statefulness|`iptables -t raw -L -n`|
|Turn off nth input|iptables -D INPUT <n>|
|Allow established connections|`iptables -A INPUT -i interface -m state --states RELATED,ESTABLISHED -j ACCEPT`|
|Change Default Policy for none matching rules|`iptables -P INPUT/FORWARD/OUTPUT ACCEPT/REJECT/DROP`|
|||

### Allow SSH on port 22 outbound

```
iptables -A OUTPUT -o iface -p tcp --dport 22 -m state --state NEW,ESTABLISHED -j ACCEPT
iptables -A INPUT -i iface -p tcp --sport 22 -m state --state ESTABLISHED -j ACCEPT
```

### Allow ICMP Outbound

```
iptacles -A OUTPUT -i iface -p icmp --icmp-t;pe echo-request -j ACCEPT
iptables -A INPUT -o iface -p icmp --icmp-tjpe echo-repl; -j ACCEPT
```

### ALLOW ONLY 1.1.1.0/24, PORTS 80,443 AND LOG DROPS TO /VAR/LOG/MESSAGES

```
iptables -A -s 1.1.1.0/24 -m state --state -p tcp -m multipart --dports 80,443 -j ACCEPT
iptables -A INPUT -i ethO -m state --state RELATED,ESTABLISHED -j ACCEPT iptables -P INPUT DROP
iptables -A OUTPUT -o ethO -j ACCEPT
iptables -A INPUT -i lo -j ACCEPT
iptables -A OUTPUT -o lo -j ACCEPT
iptables -N LOGGING
iptables -A INPUT -j LOGGING
iptables -A LOGGING -m limit --limit 4/min -j LOG --log-prefix "DROPPED " iptables -A LOGGING -j DROP
```

### Port Forward

```
echo "1" /proc/sys/net/ipv4/ip_forward
OR- SJSCtl net.lpv4.lp
iptables -t nat -A PREROUTING -p tcp -i ethO -j DNAT -d pivotip --dport 443 -to-destination attk 1p :443
iptables -t nat -A POSTROUTING -p tcp -i ethC -j SNAT -s target subnet cidr -d attackip --dport 443 -to-source pivotip iptables -t filter -I FORWARD 1 -j ACCEPT
```
