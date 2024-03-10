
notes of [@jhaddix](https://twitter.com/Jhaddix) lives

https://book.hacktricks.xyz/generic-methodologies-and-resources/external-recon-methodology

![path](https://github.com/geleiaa/Reconnaissance_notes/blob/main/imgs/path.png)

## 1 - ASNs

http://bgp.he.net

https://whois.arin.net/ui/query.do (us region)

https://apps.db.ripe.net/db-web-ui/#/fulltextsearch

https://www.whoxy.com/

https://centralops.net/co/

#### Find more principal domains (apex domains)

https://github.com/expl0itable3/check_mdi/blob/main/check_mdi.py


#### port scan in ASNs

```$ echo AS394161 | asnmap -silent | naabu -silent```

```$ echo AS394161 | asnmap -silent | naabu -silent -nmap-cli 'nmap -sV'```


## Recon in Cloud based infra

cloud ips

Amazon: http://bit.ly/2vUSjED

Azure: http://bit.ly/2r7rHeR

Google Cloud: http://bit.ly/2HAsZFm

#### cert transparecy in cloud ips

https://github.com/UnaPibaGeek/ctfr 

https://github.com/g0ldencybersec/cloudrecon (cert transparecy in cloud domains)

https://github.com/cheetz/sslScrape

parse cloudrecon tool data collected:
```$ grep -F '.DOMAIN.COM' domainfile_DB.txt | awk -F '[][]''{print $2}' | sed 's##\n#g' "DOMAIN.COM" | sort -fu | cut -d ',' -f1 | sort -u```

```$ grep -F '.DOMAIN.COM' domainfile_DB.txt | awk -F '[][]''{print $2}' | sed 's##\n#g' | sort -fu | cut -d ',' -f1 | sort -u```

https://github.com/lord-alfred/ipranges/blob/main/all/ipv4_merged.txt (cloud providers ips)

http://kaeferjaeger.gay/ (cloud providers ips)


#### resolve ips to domains via ssl cert

https://github.com/hakluke/hakip2host

```$ prips 173.0.84.0/24 | ./hakip2host```

#### sub enum

https://github.com/nsonaniya2010/SubDomainizer (sub, cloud, js)


## Shodan

![shodanrsrcs](https://github.com/geleiaa/Reconnaissance_notes/blob/main/imgs/shodanrsrc.png)

https://github.com/pirxthepilot/wtfis (passive recon)

https://github.com/Dheerajmadhukar/karma_v2 (passive recon with shodan)

https://github.com/incogbyte/shosubgo (passive subdomain recon with shodan)

#### smap port scan (shodan api free)

https://github.com/s0md3v/Smap

```$ smap DOMAIN or IP```


## Git

#### _cs.github_
 
 https://github.blog/2021-12-08-improving-github-code-search/

#### Git dorker

https://github.com/obheda12/GitDorker


#### git exposed

 ``` $ echo domain.com | subfinder -silent | httpx -silent | anew file ```
 
 ``` $ echo domain.com | subfinder -silent | xargs -I@ sh -c 'goop @ -f' ```

 https://github.com/arthaud/git-dumper
 
 https://github.com/nyancrimew/goop

#### github search

https://gist.github.com/jhaddix/1fb7ab2409ab579178d2a79959909b33

https://github.com/gwen001



## SubDomain enum

#### general enum

https://github.com/leebaird/discover

#### subdomain scraping (google, github, cloud ranges)

site:twitch.tv -www.twitch.tv
               -www.sub,twitch.tv -sub.twitch.tv

https://github.com/m3n0sd0n4ld/GooFuzz

https://github.com/darklotuskdb/sd-goo

#### Google-Fu:
Copyright text

Terms of service text

Privacy policy text

#### Favicon analysis

https://github.com/devanshbatham/FavFreak

#### Sub Takeover

https://github.com/EdOverflow/can-i-take-over-xyz

https://github.com/Ice3man543/SubOver

#### historical subdomain

- securitytrails.com
- subdomainfinder.c99.nl
- web.archive.org
- dnsdumpster.com
- github.com/Screetsec/Sudomy

#### certs e passivos

- subfinder
- certspotter https://sslmate.com/certspotter/ (free tools)
- ctfr (crt.sh) (https://github.com/UnaPibaGeek/ctfr)
- chaos.projectdiscovery.io

``` $ subfinder -d domain.com -silent | httpx -status | gau ```

``` $ subfinder -d domain | httpx -csp-probe -title ```


#### bbot tool (https://github.com/blacklanternsecurity/bbot)
parse bbot output:

```cat /root/.bbot/scans/{scan_name}/output.txt | grep -F '[DNS_NAME]' | awk '{print $2}'```

#### brute-force (only use in vps)

- sublist3r
- subbrute
- amass

#### After sub enum
after subdomain enum verify if domains is active/online

and

screeshotting: analysis all screeshot and priorize domains to test (eyewitness, aquatone, httpscreenshot)


## Pré-Manual Testing and Automation

#### Test Layers

- Open Ports and Services
- Web Hosting Software
- Application Framework
- Application Custon Code or COTS
- Application Libraries (usually javascript)
- Instagrations

#### Tech-Profiling

- webanalyze cli tool (wappalyzer)

#### Find cve's and misconfigs

- nuclei scan for vulns
- gofingerprint (Tanner Barnes)
- Sn1per (@xer0dayz)
- Intrigue Core (jcran)
- Vulners (Burp ext)
- Jaeles Scanner (j3ssi3jjj)
- retire.js

#### Service Scanning

https://github.com/x90skysn3k/brutespray

#### Port Scan

- use passive methods


## Content/Parameter/URL Discovery

- Based on tech
- COTS/PAID/OSS
(danielmiessler/Source2URL)
- Custom (github.com/0xDexter0us/Scavenger)
- Historical (echo domain.com | gau | wordlistgen | sort -u)
- Recursive (Tip: if you found a 401 dont stop, keep going and go deep)
- Mobile APIs
- Change Detection
- Technologies Tips (web servers and frameworks)

#### Tools

- turbo intruder
- Gobuster
- feroxbuster
- ParamSpider
- gf
- Parht
- kxss
- gxss
- SecretFinder
- gau (https://github.com/lc/gau)
- hakrawler
- wfuzz
- ffuf
- dirsearch
- arjun  ``` $ arjun -u url ``` (https://github.com/s0md3v/Arjun)
- https://github.com/tomnomnom/unfurl
- https://github.com/projectdiscovery/katana

``` $ cat domains.txt | httpx -status | gau ```

``` $ cat domains.txt | httpx -status -ports 80,443,8080 -path /admin ``` 

``` $ subfinder -d domain.com -silent | aquatone ``` 

``` $ cat targets | ./feroxbuster --stdin --silent -s 200 301 302 --redirects -x js | fff -s 200 -o js-files ```

``` $ echo domain | waybackurls | unfurl paths ```

``` $ echo domain | waybackurls | unfurl keys ```

``` $ echo domains | waybackurls | gf xss | hakcheckurl ```

``` $ echo domains | subfinder -silent | httpx -silent | katana -silent -d 10 | unfurl keys | uro ```


![contdisclists](https://github.com/geleiaa/Reconnaissance_notes/blob/main/imgs/contdisclists.png)


## Application Analysis

- Big Questions
  - how does the app pass data?
  - how and where does the app talk about users? 
    - where = cookies, api calls; how = uid, email,username, uuid
  - does the site have multi-users or user levels?
    - App designed for multiple customers
    - App has multiple users levels
      - Admin (cms/framework)
      - account admin
      - account user 
      - acount view
      - unauthenticated functionality
  - does the site have a unique threat model? (test PII data)
  - has there been past security research & vulns?
  - how does the app handle tries of xss, csrf, injection (sql, template, ...)

- spidering
  - zaproxy or burp
  - hakcrawler and gospider

- javascript analysis
  - find some things hardcoded
  - linkfinder
  - xnLinkFinder (@xnl-h4ck3r)
  - GAP burp ext
  - minified or obfuscated js still needs to be assessed manually

- hot areas
  - "Places" inside the application where bad things can normally happen
  - Or things i want to look at, that may indicate interesting places to explore from a hacker PoV

- parameter analysis
  - priorize parameters that were vulnerable to certain vulns classes...
  - gf of tomnomnom
  - jhaddix/sus_params

![hotareasmap](https://github.com/geleiaa/Reconnaissance_notes/blob/main/imgs/hotareasmap.png)
