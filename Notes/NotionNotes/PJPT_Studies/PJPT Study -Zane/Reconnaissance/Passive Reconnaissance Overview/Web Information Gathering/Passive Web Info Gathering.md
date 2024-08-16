# Passive Web Info Gathering

[Domain digging](Passive%20Web%20Info%20Gathering%20d9cde573ce1e498d924756accf822595/Domain%20digging%206d4e5d6e150643b88325c5d8b474215a.md)

- sublist3r: This tool enumerates subdomains for the provided domain

```jsx
apt install sublist3r

sublist3r

sublist3r -d DOMAIN
```

- crt.sh: This tool will search certificate fingerprinting for the domain provider

```jsx
%.domain.com
```

- Owasp Amass

[Https://github.com/OWASP/Amass](Https://github.com/OWASP/Amass) 

- Builtwith

This tool will expose what technology the website is built with such as the Framework

- wappalyzer

wappalyzer is a plugin built into the browser that will display the technology being ran on the website. With this data you can take the frameworks or technology being used and enumerate vulnerabilities about the technology especially since version numbers will be displayed as well

- Burp Suite

This tool is a web proxy and it has the ability to intercept web traffic. 

Step 1: Setup browser

Go to preferences on desired webpage

Go to settings

Setup Manual proxy configuration

Use this proxy for all

Navigate to [https://burp](https://burp) and download the cert

Upload cert to certificates inside preferences on browser

Import Cert

Step 2: Access Burpsuite

In burpsuite you can intercept traffic as well and get a ton of information about the website such as server names

- Google Fu
    - Google Search Syntax
        - site:domain.com -www
            - This eliminates the www. From the search
- Utilizing Social Media
    - With all the different social media methods you can find badge pictures and names through social media
    - You can compare the naming scheme to the emails found to compare names to peoples email addresses