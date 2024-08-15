# Directory Enumeration

- Directory enumeration is the act digging through directories of a webpage to expose if we can access any of them.
    - Gobuster is a tool we can use to to dig through directories, by supplying a wordlist it can compare common names

```jsx
gobuster dir -u http://IP/ --wordlist /usr/share/dirb/wordlists/common.txt
```

- Status code 200: directories directly accessible
- Status code 301: permanent redirect
- Status code 403: these resources are forbidden
    - dirsearch

```jsx
dirsearch -u http://nameofurl
```

- when we run this if we find any directories accessible we can use curl to access the webpage to see the finding

```jsx
curl http://ip/founddirectory
```

- There are many thing we can do with the information if it is accessible. Sometimes it can show version numbers, usernames, or passwords
- If an admin.php is identified we can attempt to access the page
- **The tip is to browse ALL directories and search for key information that can be found within**

If we find a list such as USERS and it has an xml format we can access that and use another tool called xmllint to make it look pretty

- we can curl to the directory as well as to the xml file

```jsx
curl -s http://ip/dir/file.xml | xmllint --format -
```

-s, silent

- The main thing with directory enumeration is to dig through all files and continue digging through all possible areas
- A command to use to grep out commands

```jsx
cat * grep
```