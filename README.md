
## Reconnaissance

Essa lista de ferramentas e tecnicas foi tirada da serie de artigos do Lucas Carmo:
* https://labs.hakaioffsec.com/reconnaissance-like-a-cyber-scout-part-1/
* https://labs.hakaioffsec.com/reconnaissance-like-a-cyber-scout-part-2/
*

Separei tudo aqui para poder ter uma consulta rapida.

>___

## OSINT:

* [WHOIS](https://github.com/rfc1036/whois) is a query and response protocol that provides information about existing domain names and their pertinent data.

* [Amass](https://github.com/OWASP/Amass) performs network mapping of attack surfaces and external asset discovery using open-source information gathering and active reconnaissance techniques. Already does this and other features.


#### Information gathering through Search Engines/Social Media:

It consists of searching public information like *email addresses*, *usernames*, *hosts*, *links*, and other things that are public on the internet. This search takes place through services such as *anubis*, *baidu*, *bevigil*, *binaryedge*, *bing*, *bingapi*, *bufferoverun*, *censys*, *certspotter*, *crtsh*, *dnsdumpster*, *duckduckgo*, *fullhunt*, *github-code*, *hackertarget*, *hunter*, *intelx*, *otx*, *pentesttools*, *projectdiscovery*, *qwant*, *rapiddns*, *rocketreach*, *securityTrails*, *sublist3r*, *threatcrowd*, *threatminer*, *urlscan*, *virustotal*, *yahoo*, and *zoomeye*. The important thing is to use these search engines as much as possible to find these values.

* [theHarvester](https://github.com/laramies/theHarvester) is a powerful tool designed to be used during the reconnaissance stage of a red team assessment or penetration test. It performs open source intelligence (OSINT) gathering to help determine a domain's external threat landscape. The tool gathers names, emails, IPs, subdomains, and URLs by using multiple public resources.

* [EmailFinder](https://github.com/Josue87/EmailFinder) is designed to find company emails that are filtered by search engines. This is done by searching for @company.com. The goal has to be to have the minimum amount of emails in the search engines.


#### Password leaks:

Password leaks can help us understand the pattern of passwords used by a user or even reuse them. This search is carried out through database services that verify whether the e-mail used is part of a leak.

[h8mail](https://github.com/khast3x/h8mail) is an email OSINT and breach hunting tool using different breach and reconnaissance services, or local breaches such as Troy Hunt's "Collection1" and the infamous "Breach Compilation" torrent.


#### Metadata finder ([MetaFinder](https://github.com/Josue87/MetaFinder)):
searches for documents in a domain through Search Engines. The objective is to extract metadata.

#### Google Dorks: [dorks_hunter](https://github.com/six2dez/dorks_hunter)

#### Github Dorks:
[gitdorks_go](https://github.com/damit5/gitdorks_go)GitDorker can be used with additional tools such as GitRob or Trufflehog on interesting repositories or users discovered from GitDorker to produce the best results.

#### GitHub org analysis:
* [Enumerepo](https://github.com/trickest/enumerepo) List all public repositories for (valid) GitHub usernames. [Trufflehog](https://github.com/trufflesecurity/trufflehog) Find leaked credentials.

>___

## Subdomain Enumeration:

#### Passive enum

Passive enumeration is an information-gathering technique without directly interacting with the target. This includes searching the internet for public data such as IP addresses, domain names, and information about technologies used to gain a more comprehensive understanding of the target system or network.

* [Amass](https://github.com/OWASP/Amass)
* [Subfinder](https://github.com/projectdiscovery/subfinder)
* [github-subdomains](https://github.com/gwen001/github-subdomains) find subdomains on GitHub.


#### Certificate transparency:

Certificate Transparency is an SSL/TLS certificate security mechanism that seeks to make the issuance and use of certificates more transparent and secure. It works by recording all certificates issued for a specific domain in public records, which can be checked by anyone. This helps detect fraudulent certificate issuance, ensuring end users are confident they are connecting to a legitimate and secure website. In addition, it also provides a mechanism to detect and resolve certificate revocations.

* [Ctfr](https://github.com/UnaPibaGeek/ctfr) allows getting the subdomains from an HTTPS website in a few seconds.
How does it work? CTFR does not use a dictionary attack nor brute force, it just abuses of Certificate Transparency logs.

#### NOERROR subdomain discovery:

NOERROR Subdomain Discovery is a discovery technique based on the DNS server's response to null (empty) requests. It takes advantage of the default configuration of DNS servers that respond with a NOERROR status even when a request does not find a valid entry in the name database. By performing a series of DNS requests with hypothetical subdomain names, it is possible to identify existing subdomains that return the NOERROR status.

* [Dnsx](https://github.com/projectdiscovery/dnsx) is a fast and multi-purpose DNS toolkit designed for running various probes through the [retryabledns](https://github.com/projectdiscovery/retryabledns) library. It supports multiple DNS queries, user-supplied resolvers, and DNS wildcard filtering.

#### DNS Bruteforce: 

[Puredns](https://github.com/d3mondev/puredns) is a fast domain resolver and subdomain brute-forcing tool that can accurately filter out wildcard subdomains and DNS-poisoned entries.


### Permutaions: 

Permutations are used in various fields, including cryptography, artificial intelligence, and algorithmic research, to test all possible combinations of input and find the best solution for a given problem. In our case, permutations are used in brute force tests, where we try to find a solution through trial and error of all possible combinations.

* [Gotator](https://github.com/Josue87/gotator) is a tool to generate DNS wordlists through permutations. 

* [Ripgen](https://github.com/resyncgg/ripgen) generates a combination of domain names from the provided input. Combinations are created based on a wordlist and are based on Rust.

* [Regulator](https://github.com/cramppet/regulator) with automated learning of regexes for DNS discovery.


### Scraping/Spidering/Crawling

A web spider, also known as a crawler is a computer program that is used to automatically traverse the World Wide Web (WWW) and collect information from web pages. It works by downloading web pages, following links on downloaded pages, and collecting relevant information such as email addresses, images, links, and page content.

[Gospider](https://github.com/jaeles-project/gospider)


#### Google Analytics: [AnalyticsRelationships](https://github.com/Josue87/AnalyticsRelationships)



#### TLS or SSL handshake (tlsx) ...

#### Recursive search:

Recursive search is a search technique used in programming and artificial intelligence, where a function calls itself to perform the search. In other words, the function performs the search repeatedly until it finds the desired solution or until it reaches a stop condition.

* [Dsieve](https://github.com/trickest/dsieve) takes a single domain or reads an input file and extract unique parent domains, enrich subdomains, filter subdomains by level, or find out which subdomains have the most number of sub-subdomains (or sub-sub-subdomains or sub-sub-sub...). Dsieve supports any format of URL, with or without protocol, port, path, and parameters.



#### Subdomains takeover:

Subdomain takeover is a vulnerability that allows an attacker to take control of a subdomain. This occurs when the same is no longer being used or managed by the original owner but is still pointing to a third-party service such as a hosting provider or CDN service.

* [Nuclei](https://github.com/projectdiscovery/nuclei)

* [Dnstake](https://github.com/pwnesia/dnstake) uses [RetryableDNS](https://github.com/projectdiscovery/retryabledns) client library to send DNS queries. Initiates engagement using Google & Cloudflare DNS as the resolver, then check and fingerprints the nameservers of the target host - if there is one, it will resolve the target host again with its nameserver IPs as resolver, if it gets a weird DNS status response (other than NOERROR/NXDOMAIN), then it's vulnerable to being taken over.


####  DNS Zone Transfer:

DNS Zone Transfer is a feature of the Domain Name System (DNS) protocol that allows replication of DNS record information from a primary server to one or more secondary servers. It is an important process for ensuring the availability and consistency of DNS record information throughout the network.

* [Dig](https://linux.die.net/man/1/dig) (domain information groper) is a flexible tool for interrogating DNS name servers. It performs DNS lookups and displays the answers that are returned from the name server(s) that were queried. Most DNS administrators use dig to troubleshoot DNS problems because of its flexibility, ease of use, and clarity of output.


#### Cloud checkers:

Cloud checkers is a term that refers to tools that check the security configuration of a cloud, usually to identify vulnerabilities or configuration errors that could affect the security of data stored in the cloud. These tools can scan the security configuration of a cloud such as Amazon Web Services (AWS), Microsoft Azure, or Google Cloud Platform (GCP) and provide detailed reports on any identified security issues.

#### ...

## HOSTS