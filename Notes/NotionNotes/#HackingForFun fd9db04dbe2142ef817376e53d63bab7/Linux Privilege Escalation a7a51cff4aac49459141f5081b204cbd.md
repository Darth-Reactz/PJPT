# Linux Privilege Escalation

- If we need to move a file to an area where we need to wget it from our machine, look for the html/web directory on the machine and where the public facing directories are held to move the file there and quickly wget it
- The command below will upgrade you shell once you have access a shell of a victim

```php
python3 -c 'import pty; pty.spawn("/bin/bash")'
```

- Google CVE’s on versions of shell you are running to execute a possible PoC available to pwn the machine for you
- A trick is to run the below command to check and see what sudo privs you have
    
    ```jsx
    sudo -l
    ```
    
- If there is no results from sudo -l, check version number of terminal you are in
- gtfobins
    - this website can help us find ways to get a root shell by using sudo against a file we have permissions over
- We can run a tool called [LinEnum.sh](http://LinEnum.sh) or Linpeas to perform automated privilege escalation checks.
    - You must download this tool to the local attack VM
- A good trick is that to get to root user if you have the password is

```jsx
su root
```