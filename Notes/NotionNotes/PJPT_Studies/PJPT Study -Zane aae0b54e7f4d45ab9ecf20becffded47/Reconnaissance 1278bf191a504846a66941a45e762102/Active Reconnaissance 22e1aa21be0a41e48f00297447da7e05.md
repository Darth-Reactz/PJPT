# Active Reconnaissance

- nmap

```jsx
nmap -T4 -p- -A IPADDRESS
```

-t4 is speed

-p- is all ports

-A is to scan for all information about the system

- This will return open ports as well version numbers and ciphers supported
- if port 80 and/or 443is open hosting a website. Navigate to the IP address in a browser
- Nikto: Web Vulnerability Scanning

```jsx
nikto -h http://IPADDRESS
```

- dirbuster: web application brute forcing
    - What this tool does is it tries to navigate to different directories under that website to expose data.
    - If running IIS you might look for file types such as aspx

```jsx
dirbuster&
```

- Type in target IP with port attached
    - Http://IPADDRESS:Port
    - Dig down to dirbuster directory and select small.txt
- Msfconsole:
    - You can use metasploit to use auxiliary to use modules such as smb version of the protocol
- smbclient: this tool will attempt to connect to the file share Anonymously

```jsx
smbclient -L \\\\IPADDRESS\\
```

-L will list admin shares

```jsx
smbclient \\\\IPADDRESS\\ADMIN$
```

This will attempt to connect to the admin share folder

- SSH
    - With enumerating SSH you can potentially expose a banner while attempting connecting
    - Try to ssh into the IP
    
    ```jsx
    ssh IPADDRESS
    
    ssh IPADDRESS -oKexAlgorithms=+ALGORITHM
    
    ssh IPADDRESS -oKexAlgorithms=+ALGORITHM -c CIPHER
    ```