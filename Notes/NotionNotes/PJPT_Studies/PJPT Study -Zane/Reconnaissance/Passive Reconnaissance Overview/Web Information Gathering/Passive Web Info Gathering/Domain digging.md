# Domain digging

- Certificate Transparency

```jsx
curl -s https://crt.sh/\?q\=domain\&output\=json | jq .

curl -s https://crt.sh/\?q\=domain\&output\=json | jq . | grep name | cut -d":" -f2 | grep -v "CN=" | cut -d'"' -f2 | awk '{gsub(/\\n/,"\n");}1;' | sort -u
```

The first returns the results of the [crt.sh](http://crt.sh) of the domain you enter.

The second will return unique subdomains of the domain provided

- With the subdomains we can find company hosted web servers and IP address

```jsx
for i in $(cat subdomainlist);do host $i | grep "has address" | grep domain | cut -d" " -f1,4;done
```