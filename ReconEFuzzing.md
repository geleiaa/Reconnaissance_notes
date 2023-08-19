## DNS

A -> ipv4
AAAA -> ipv6
CNAME -> domains
TXT -> notes/text
MX -> email servers
SOA -> domains validations
NS -> authority servers

#### dig 

- https://www.cyberciti.biz/faq/linux-unix-dig-command-examples-usage-syntax/
- https://www.thegeekstuff.com/2012/02/dig-command-examples/
- https://www.hostinger.com/tutorials/how-to-use-the-dig-command-in-linux/


# SubDomain Enum

### Historico de subdomain

- securitytrails.com
- subdomainfinder.c99.nl
- web.archive.org
- dnsdumpster.com
- github.com/Screetsec/Sudomy


### brute-force

- sublist3r
- subbrute
- amass

### certs e passivos

- subfinder
- certspotter
- ctfr (crt.sh)
- chaos.projectdiscovery.io

``` $ subfinder -d domain.com -silent | httpx -status | gau ```

## URL Discovery 

- gau
- hakrawler
- wfuzz
- ffuf
- dirsearch

``` $ cat domains.txt | httpx -status | gau ```

## Content Discovery

- httpx
- aquatone
- SecretFinder

``` $ cat domains.txt | httpx -status -ports 80,443,8080 -path /admin ``` 

``` $ subfinder -d domain.com -silent | aquatone ```  

## Parameter discovery

- ParamSpider
- gf
- Parht
- kxss
- gxss

``` $ python3 paramspider.py -d | kxss ```

``` $ wfuzz -c -w burp-parameter-name.txt http://domain/index.php?FUZZ=test ```
``` $ wfuzz -c -w burp-parameter-name.txt http://domain/index.php?search=FUZZ ```


