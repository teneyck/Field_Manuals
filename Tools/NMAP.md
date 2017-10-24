# NMAP

Ping sweep for network:

`nmap -sn -PE <IP ADDRESS OR RANGE>`

Scan and Show Open Ports:

`nmap --open <IP ADDRESS OR RANGE>`

Determine Open Services:

`nmap -sV <IP ADDRESS>`

Scan two common TCP ports, HTTP and HTTPS:

`nmap -p 80,443 <IP ADDRESS OR RANGE>`

Scan common UDP port, DNS:

`nmap -sU -p 53 <IP ADDRESS OR RANGE>`

Scan UDP and TCP together, be verbose on a single host snd include optiona; skip ping:

`nmap -v -Pn -sU -sT -p U:53,111,137,T:21-25,80,139,8080 <IP ADDRESS>`
