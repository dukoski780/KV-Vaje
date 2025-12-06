# Lab01 - Uvod v Kali Linux

## 1. Namestitev Kali Linux

**Uporabljena metoda:**
- VirtualBox

## 2. Raziskovanje grafičnega okolja

**Grafično okolje:** Xfce

**5 varnostnih orodij, ki sem jih našel:**
1. Nmap - network scanner
2. John the Ripper - password cracker
3. Searchsploit - exploit database
4. Dnsenum - DNS enumeration
5. Tcpdump - network packet analyzer

## 3. Osnovni ukazi

### whoami
```bash
whoami
```
**Rezultat:**
```
kali
```

### hostnamectl
```bash
hostnamectl
```
**Rezultat:**
```
 Static hostname: kali
       Icon name: computer-vm
         Chassis: vm 🖴
      Machine ID: 686fa41363f049e9a84be345a7078e04
         Boot ID: 1dc1a77d2ebf45ec9b200ab4b1c65ac9
  Virtualization: oracle
Operating System: Kali GNU/Linux Rolling
          Kernel: Linux 6.12.38+kali-amd64
    Architecture: x86-64
 Hardware Vendor: innotek GmbH
  Hardware Model: VirtualBox
```

### uname -a
```bash
uname -a
```
**Rezultat:**
```
Linux kali 6.12.38+kali-amd64 #1 SMP PREEMPT_DYNAMIC Kali 6.12.38-1kali1 (2025-08-12) x86_64 GNU/Linux
```

### df -h
```bash
df -h
```
**Rezultat:**
```
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1        79G   15G   60G  20% /
tmpfs           987M  4.0K  987M   1% /dev/shm
tmpfs           987M   24K  987M   1% /tmp
```

### ip a
```bash
ip a
```
**Rezultat:**
```
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host noprefixroute
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 08:00:27:1f:b7:23 brd ff:ff:ff:ff:ff:ff
    inet 10.0.2.15/24 brd 10.0.2.255 scope global dynamic noprefixroute eth0
    inet6 fd17:625c:f037:2:e527:15bc:6bb0:dbae/64 scope global dynamic noprefixroute
    inet6 fe80::913e:c8cf:aa80:5ac9/64 scope link noprefixroute
```

### wget
```bash
wget https://gist.githubusercontent.com/EdwardRayl/3436572afde8ce9e3faf5b7b95356a49/raw/6b25895fce480713560829dec31ac8220ffe5272/gists.txt
```
**Rezultat:**
```
Resolving gist.githubusercontent.com (gist.githubusercontent.com)... 185.199.110.133, 185.199.111.133, 185.199.108.133
Connecting to gist.githubusercontent.com (gist.githubusercontent.com)|185.199.110.133|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 9634 (9.4K) [text/plain]
Saving to: 'gists.txt'

gists.txt           100%[================>]   9.41K  --.-KB/s    in 0.003s

'gists.txt' saved [9634/9634]
```

### apt install
```bash
sudo apt install 7zip
```
**Rezultat:**
```
7zip is already the newest version (25.01+dfsg-2).
```

### which (preverjanje orodij)
```bash
which nmap
which john
```
**Rezultat:**
```
/usr/bin/nmap
/usr/sbin/john
```

### htop
```bash
sudo apt install htop
htop
```
**Rezultat:**
```
Error: Unable to locate package htop
```

### traceroute
```bash
sudo apt install traceroute -y
traceroute google.com
```
**Rezultat:**
```
traceroute is already the newest version (1:2.1.6-1).
google.com: Temporary failure in name resolution
```

### nload
```bash
sudo apt install nload -y
nload
```
**Rezultat:**
```
Error: Unable to locate package nload
```

### strings
```bash
strings /bin/ls | head
```
**Rezultat:**
```
!/lib64/ld-linux-x86-64.so.2
_ITM_deregisterTMCloneTable
__gmon_start__
_ITM_registerTMCloneTable
fgetfilecon_raw
fgetfilecon
freecon
lgetfilecon
lgetfilecon_raw
_IO_stdin_used
```

## 4. Uporaba varnostnih orodij

### speedtest-cli
```bash
sudo apt install speedtest-cli -y
speedtest-cli --secure
```
**Rezultat:**
```
Error: Unable to locate package speedtest-cli
```

### tcpdump
```bash
sudo tcpdump -c 10
```
**Rezultat:**
```
listening on eth0, link-type EN10MB (Ethernet), snapshot length 262144 bytes
13:50:39.696177 IP6 fd17:625c:f037:2:2384:2f58:40de:f5a9.49138 > fd17:625c:f037:2::3.domain: 48798+ AAAA? location.services.mozilla.com.
13:50:39.700808 IP6 fe80::2 > fd17:625c:f037:2:2384:2f58:40de:f5a9: ICMP6, destination unreachable
10 packets captured
20 packets received by filter
0 packets dropped by kernel
```

### nmap
```bash
nmap 127.0.0.1
```
**Rezultat:**
```
Starting Nmap 7.95 ( https://nmap.org ) at 2025-12-06 13:50 EST
Nmap scan report for localhost (127.0.0.1)
Host is up (0.00s latency).
All 1000 scanned ports on localhost (127.0.0.1) are in ignored states.
Not shown: 1000 closed tcp ports (reset)

Nmap done: 1 IP address (1 host up) scanned in 0.26 seconds
```

### searchsploit
```bash
searchsploit wordpress ftp
```
**Rezultat:**
```
 Exploit Title                             |  Path
------------------------------------------- ---------------------------------
WordPress Plugin MiwoFTP 1.0.5 - Arbitrary | php/webapps/36774.txt
WordPress Plugin MiwoFTP 1.0.5 - Arbitrary | php/webapps/36801.txt
WordPress Plugin MiwoFTP 1.0.5 - Cross-Sit | php/webapps/36761.txt
WordPress Plugin MiwoFTP 1.0.5 - Cross-Sit | php/webapps/36763.txt
WordPress Plugin MiwoFTP 1.0.5 - Multiple  | php/webapps/36762.txt
```

### dnsenum
```bash
dnsenum google.com
```
**Rezultat:**
```
dnsenum VERSION:1.3.1
-----   google.com   -----

Host's addresses:
google.com.                              87       IN    A        142.250.180.142

Name Servers:
ns1.google.com.                          6885     IN    A        216.239.32.10
ns2.google.com.                          6647     IN    A        216.239.34.10
ns3.google.com.                          6008     IN    A        216.239.36.10
ns4.google.com.                          6969     IN    A        216.239.38.10

Mail (MX) Servers:
smtp.google.com.                         22       IN    A        142.251.31.27
smtp.google.com.                         22       IN    A        172.217.218.26

Brute forcing with /usr/share/dnsenum/dns.txt:
www.google.com.                          282      IN    A        142.250.180.164
mail.google.com.                         20       IN    A        142.251.140.101
blog.google.com.                         300      IN    CNAME    www.blogger.com.
```

### lbd
```bash
lbd google.com
```
**Rezultat:**
```
lbd - load balancing detector 0.4

Checking for DNS-Loadbalancing: NOT FOUND
Checking for HTTP-Loadbalancing [Server]: gws NOT FOUND
Checking for HTTP-Loadbalancing [Diff]: FOUND

google.com does Load-balancing. Found via Methods: HTTP[Diff]
```

### name-that-hash
```bash
sudo apt install name-that-hash
nth -t ef487f75307f96954d3bb132e5f4b035
```
**Rezultat:**
```
ef487f75307f96954d3bb132e5f4b035

Most Likely
MD5, HC: 0 JtR: raw-md5 Summary: Used for Linux Shadow files.
MD4, HC: 900 JtR: raw-md4
NTLM, HC: 1000 JtR: nt Summary: Often used in Windows Active Directory.
Domain Cached Credentials, HC: 1100 JtR: mscach

Least Likely
Double MD5, HC: 2600
md5(md5(md5($pass))), HC: 3500
md5(sha1($pass)), HC: 4400
RIPEMD-128, JtR: ripemd-128
```

## 5. Refleksija in analiza

**Zakaj uporabljamo Kali Linux? Kaj je prednost Kali Linux v primerjavi z ostalimi Linux distribucijami?**

Kali Linux je namenjen preverjanju informacijske varnosti, ker vključuje veliko specializiranih orodij za testiranje omrežij, sistemov in spletnih aplikacij.
V primerjavi z drugimi distribucijami ponuja prednost predvsem v tem, da so orodja za varnost že pripravljena za uporabo, redno posodobljena in jih lahko poganjamo tudi kot "live" okolje ali v navideznem stroju.

**Katere funkcionalnosti in orodja Kali Linuxa so vas najbolj pritegnile?**

Najbolj izstopajo orodja, ki omogočajo hiter vpogled v stanje varnosti:
Nmap za pregled omrežnih vrat, Searchsploit za odkrivanje znanih ranljivosti, Dnsenum za zbiranje informacij o domenah ter Name-That-Hash za prepoznavanje hash algoritmov.
