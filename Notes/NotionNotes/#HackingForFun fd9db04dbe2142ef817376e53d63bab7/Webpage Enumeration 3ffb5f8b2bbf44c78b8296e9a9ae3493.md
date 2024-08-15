# Webpage Enumeration

- If we find a webpage being ran on a server, first look up exploits on the backend of the webpage, try to find version number being ran as well
- we can run a script to enumeration common web application directories

```jsx
nmap -sv --script=http-enum -oA nameofFile ip
```

- Once we have determined that port 80 is open we can begin the process of footprinting

WhatWeb is a tool to identify the web application in use

```jsx
whatweb ip

whatweb http://ip/directory
```

- If we browse to the page it is a good trick to check the source code. Or we can run curl
    - we can also execute code with curl by curling to the full path

```jsx
curl http://ip
```