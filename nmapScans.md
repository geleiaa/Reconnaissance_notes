## Fast network range/subnet scan (adapt flags)

nmap -sS -Pn --host-timeout=1m --max-rtt-timeout=600ms /
--initial-rtt-timeout=300ms --min-rtt-timeout=300ms /
--stats-every 10s --top-ports 500 --min-rate 1000 /
--max-retries 0 -n -T5 --min-hostgroup 255 -oA fast_scan_output -iL TARGET_NET

This Nmap scan will enumerate the top 500 TCP ports, only sends the first half of the TCP handshake, and assumes all hosts are up. There is also a bit of fine-tuned timing, the -T5 takes care of all the base settings, and we drop the rtt-timeout down to 300ms, add a 1m host timeout, do not reattempt any ports, turn the minimum sending rate up to 1000, and scan 255 hosts at a time.


## Stealth host scan  ??????? ids/ips/fw bypass ???????

all scans here are slow and should only be used for one host, if you use it to enumerate an IP range/subnet, well, you know...

#### Netcat scan

nc -nvv -w 1 -z TARGETIP 1000-2000
nc -nv -u -z -w 1 TARGETIP 160-162

#### Slow Scan 

https://nmap.org/book/performance-timing-templates.html

nmap -T paranoid or 0
nmap -T sneaky or 1 
nmap --scan-delay 10s

#### FIN scan + slow + fragm

nmap -vv -n -sF -f -T paranoid TARGETIP

#### Xmas scan + slow + fragm

nmap -vv -n -sX --mtu 32 -T sneaky TARGETIP

#### NULL scan + slow + fragm

nmap -vv -n -sN -f -T paranoid TARGETIP

#### spoofing IP and MAC + slow + frag + decoy

nmap -vv -n -D RND:5 -f -T sneaky TARGETIP 
nmap -vv -n --spoof-mac 0 -f -T sneaky TARGETIP
nmap -vv -n -Pn -f -S FAKEIP -e NETINFTERFACE -T paranoid TARGETIP
nmap -vv -n -sF -f -D RND: 5 -T paranoid TARGETIP
hping TARGETIP -a FAKEIP

### source-port + fragm + slow

nmap -vv -n -g 53 --mtu 40 -T sneaky TARGETIP

#### random hosts + fragm + slow

nmap -vv -n -Pn -g 53 --mtu 40  --randomize-hosts -T sneaky TARGETIP


#### packets Manipulation

nmap --data 0xdeadbeef
nmap --data-string “my l33t skills”
nping --icmp --icmp-type 3 --icmp-code 1 --source-ip IP --dest-ip IP --icmp-id 720 --icmp-seq 0 --data-string 'some text'

#### random bytes
nmap -vv -n -Pn --data-length 36 -f -S FAKEIP -e NETINFTERF -T paranoid TARGETIP

#### TTL Manipulation

...


#### firewalking
custom packets, traceroute + port scan, firewalk tool, inverse tpc flags(xmas, FIN, NULL, Maimon)


#### Anonymize ?????
Idle scan
FTP bounce scan
https://eller.arizona.edu/sites/default/files/rodney_rorhmann_sfs_masters_paper.pdf
https://github.com/alkasir/alkasir

proxy chain => proxy switcher, proxifier, proxy workbench, proxychains, some vps, vpn????
https://0x00sec.org/t/whats-the-most-anonymous-active-scanning-technique/5678/6




#### Finding hosts

https://www.shodan.io/

https://en.fofa.info/

https://viz.greynoise.io/

https://www.zoomeye.org/

https://search.censys.io/

https://ivre.rocks/#get-started

https://www.criminalip.io/

https://www.binaryedge.io/


refs:

https://nmap.org/book/toc.html

https://nmap.org/book/firewall-subversion.html

https://book.hacktricks.xyz/generic-methodologies-and-resources/pentesting-network/ids-evasion

https://github.com/jesusgavancho/TryHackMe_and_HackTheBox/blob/master/Firewalls.md

https://www.giac.org/paper/gsec/1985/stealth-port-scanning-methods/103446

https://infosecwriteups.com/evading-firewall-ids-during-network-reconnaissance-using-nmap-7dc393138178

https://medium.com/@IamLucif3r/top-10-firewall-ids-evasion-techniques-cb1e1cc06f24

https://www.youtube.com/watch?v=I0VSp7h0eb4 

https://github.com/gnebbia/nmap_tutorial/blob/master/sections/detecting_and_evading_a_firewall.md

https://ocholuo.github.io/posts/IDS-Evasion-Techniques/

