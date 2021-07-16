![Logo](https://i.imgur.com/PyKLAe7.png)

[![License](https://img.shields.io/badge/license-The_Unlicense-red.svg)](https://unlicense.org/)

About
----

**IPsum** is a threat intelligence feed based on 30+ different publicly available [lists](https://github.com/stamparm/maltrail) of suspicious and/or malicious IP addresses. All lists are automatically retrieved and parsed on a daily (24h) basis and the final result is pushed to this repository. List is made of IP addresses together with a total number of (black)list occurrence (for each). Greater the number, lesser the chance of false positive detection and/or dropping in (inbound) monitored traffic. Also, list is sorted from most (problematic) to least occurent IP addresses.

As an example, to get a fresh and ready-to-deploy auto-ban list of "bad IPs" that appear on at least 3 (black)lists you can run:

```
curl --compressed https://raw.githubusercontent.com/stamparm/ipsum/master/ipsum.txt 2>/dev/null | grep -v "#" | grep -v -E "\s[1-2]$" | cut -f 1
```

If you want to try it with `ipset`, you can do the following:

```
sudo su
apt -qq install iptables ipset
ipset -q flush ipsum
ipset -q create ipsum hash:net
for ip in $(curl --compressed https://raw.githubusercontent.com/stamparm/ipsum/master/ipsum.txt 2>/dev/null | grep -v "#" | grep -v -E "\s[1-2]$" | cut -f 1); do ipset add ipsum $ip; done
iptables -I INPUT -m set --match-set ipsum src -j DROP
```

In directory [levels](levels) you can find preprocessed raw IP lists based on number of blacklist occurrences (e.g. [levels/3.txt](levels/3.txt) holds IP addresses that can be found on 3 or more blacklists).

Wall of Shame (2021-07-16)
----

|IP|DNS lookup|Number of (black)lists|
|---|---|--:|
141.98.10.179|er.includeswitche.com|10
171.25.193.25|tor-exit5-readme.dfri.se|10
209.141.42.147|-|9
161.35.80.11|-|9
171.25.193.78|tor-exit4-readme.dfri.se|9
199.195.248.154|-|9
205.185.119.90|email-poczta.pl|8
205.185.126.160|-|8
209.141.50.25|peach.snapnode.com|8
205.185.121.179|-|8
205.185.125.109|-|8
107.189.1.174|-|8
209.141.54.66|-|8
209.141.62.234|-|8
205.185.126.8|-|8
141.98.10.29|-|8
107.189.1.180|-|8
141.98.10.203|-|8
64.113.32.29|tor.t-3.net|8
134.122.63.163|-|8
62.210.105.116|62-210-105-116.rev.poneytelecom.eu|8
199.19.226.109|-|7
128.31.0.13|tor-exit.csail.mit.edu|7
221.131.165.23|-|7
209.141.53.8|-|7
222.187.232.205|-|7
107.189.6.214|-|7
104.244.78.233|This-is-a-tor-exit.ignorelist.com|7
107.189.1.161|-|7
221.131.165.56|-|7
209.141.60.49|-|7
178.20.55.16|marcuse-1.nos-oignons.net|7
162.247.72.199|jaffer.tor-exit.calyxinstitute.org|7
221.181.185.140|-|7
221.181.185.143|-|7
185.220.100.254|tor-exit-3.zbau.f3netze.de|7
185.107.70.202|tor-exit.r3.darknet.dev|7
192.42.116.16|tor-exit.hartvoorinternetvrijheid.nl|7
166.70.207.2|this.is.a.tor.node.xmission.com|7
222.187.239.109|-|7
42.192.69.45|-|7
185.130.44.108|tor-exit-se1.privex.cc|7
222.186.42.7|-|7
176.10.104.240|tor1e1.digitale-gesellschaft.ch|7
107.189.3.151|-|7
221.181.185.223|-|7
1.15.92.61|-|7
107.189.2.212|-|7
107.189.28.77|-|7
221.181.185.159|-|7
107.189.30.250|-|7
221.181.185.153|-|7
171.251.26.14|dynamic-ip-adsl.viettel.vn|7
45.153.160.133|-|7
45.153.160.132|-|7
222.186.42.13|-|7
104.244.79.229|localhost|7
77.247.181.163|lumumba.torservers.net|7
51.15.43.205|tor4thepeople3.torexitnode.net|7
104.244.72.14|14.72.244.104.network.tld|7
162.247.74.206|rosaluxemburg.tor-exit.calyxinstitute.org|7
205.185.127.25|serveroperations.com|7
89.234.157.254|marylou.nos-oignons.net|7
221.181.185.198|-|7
36.112.171.51|-|7
222.186.30.112|-|7
221.181.185.19|-|7
190.56.224.166|166.224.56.190.dynamic.intelnet.net.gt|7
107.189.1.144|-|7
171.25.193.77|tor-exit1-readme.dfri.se|7
185.220.101.9|-|7
185.220.101.4|-|7
185.220.101.1|-|7
209.141.32.39|-|7
107.189.30.47|-|7
116.98.169.131|dynamic-ip-adsl.viettel.vn|7
107.189.1.107|-|7
62.210.37.82|62-210-37-82.rev.poneytelecom.eu|7
222.186.42.213|-|7
222.186.42.137|-|7
185.220.101.22|-|7
221.181.185.151|-|7
143.110.221.59|-|7
221.181.185.220|-|7
198.144.121.93|-|7
222.186.180.130|-|7
104.244.76.206|-|7
107.189.3.138|-|7
107.189.10.140|mail.swiftsmtp.com|7
205.185.125.24|-|7
176.10.99.200|accessnow.org|7
222.187.238.136|-|7
205.185.117.79|-|7
222.168.30.19|-|7
222.186.30.76|-|7
167.99.34.181|-|7
167.99.176.15|-|7
199.19.226.145|lv01.0wn.net|7
221.181.185.135|-|7
209.141.35.160|mail.g3nius.org|7
80.67.172.162|algrothendieck.nos-oignons.net|7
