# Basic Enumeration for General Knowledge of Target

![Untitled](Basic%20Enumeration%20for%20General%20Knowledge%20of%20Target%20835f36842b034b55833e44deca9e883c/Untitled.png)

- Start with this nmap command to gain knowledge of what ports are open

```jsx
sudo nmap -n -Pn -p- IP
```

- Run this nmap after knowing what ports are opened to gain more info

```jsx
sudo nmap -n -Pn -pPORTS -sV -sC IP -oA sau_ports
```

- If webpage is found google exploits with the website.
    - Move laterally until you can find a CVE or opportunity to get shell access

```jsx
nmap -sV --open -oA nameofFile ip
```

- nmap scan device to determine open ports against device

-sV,  probes open ports to determine service/version number

—open, only show open

-oA, outputs in three major file formats

- Alternately you can run

```jsx
nmap -p- --open -oA nameofFile ip
```

The -p- will scan all 65,535 ports

- The Nmap command below will slim down the results and only return to the screen the IP’s found

```jsx
sudo nmap IP -sn -oA tnet | grep for | cut -d" " -f5
```

-sn disables port scanning

- nmap using ICMP

```jsx
sudo nmap IP -sn -oA host -PE --packet-trace
```

-PE, uses ICMP 

—packet-trace, shows all the packets being sent

- Adds a reasoning to the scan

```jsx
sudo nmap IP -sn -oA host -PE --reason
```

—reason, reason why the host is up

- This forces the device to use ICMP instead of ARP

```jsx
sudo nmap IP -sn -oA host -PE --packet-trace --disable-arp-ping
```

—disable-arp-ping

- This scan uses the TCP three-way handshake to determine if the target host is open or closed

```jsx
sudo nmap IP -p 443 --packet-trace --disable-arp-ping -Pn -n --reason -sT
```

-sT, Uses TCP connect scan

```jsx
sudo nmap IP -p PORT -sS -Pn -n --disable-arp-ping --packet-trace -D RND:5
```

-D RND:5, generates 5 random IP’s

-n, disables DNS resolution

-Pn, disables ICMP

- IPS/IDS evasion DNS Server Version

```jsx
sudo nmap -sU -p 53 --script dns-nsid IP
```

-sU, UDP 

—script dns-nsid, request the name server version using UDP

- Netcat can be used to grab versions of running services using the DNS port

```jsx
sudo nc -nv -p 53 IP PORT
```

- Netcat can be used to do banner grabbing which can let us know more versions of things the ports are running

```jsx
nc -nv ip port
```