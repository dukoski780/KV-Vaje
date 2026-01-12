# Lab09 - Testiranje SSH varnosti z Nmap in Hydra




```
Starting Nmap 7.95 ( https://nmap.org ) at 2026-01-06 13:43 EST
Nmap scan report for 172.17.0.2
Host is up (0.00013s latency).
Not shown: 65534 closed tcp ports (reset)
PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 8.9p1 Ubuntu 3ubuntu0.13 (Ubuntu Linux; protocol 2.0)
MAC Address: 02:42:AC:11:00:02 (Unknown)
Device type: general purpose|router
Running: Linux 4.X|5.X, MikroTik RouterOS 7.X
OS details: Linux 4.15 - 5.19, OpenWrt 21.02 (Linux 5.4)
Network Distance: 1 hop
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

Nmap done: 1 IP address (1 host up) scanned in 2.65 seconds
```


---

## Refleksija

**Zakaj je uporaba šibkih gesel nevarna in zakaj zapirati neuporabljene porte?**

Šibka gesla so nevarna, ker so ranljiva za avtomatizirane napade. Pogosto se pojavljajo na seznamih pogostih gesel, kar omogoča hitro razbijanje z orodji kot je Hydra. Brute force napadi jih lahko razkrijejo v nekaj sekundah ali minutah. Zapiranje neuporabljenih portov zmanjšuje napadalno površino. Manj kot je odprtih portov, manj je priložnosti za napad. Vsaka odprta storitev predstavlja potencialno ranljivost.

**Kako bi zaščitili SSH strežnik pred brute-force napadi?**

SSH strežnik bi zaščitili s spremembo privzetega porta na nestandarden port, kar zmanjša avtomatizirane napade. Uporabiti bi morali močna gesla ali še bolje javno-zasebne ključe, ki brute force napad naredijo neučinkovit. Omejiti bi morali število poskusov prijave z orodji kot je fail2ban, ki začasno blokira IP naslove po večih neuspelih poskusih.

**Katere dodatne ukrepe bi priporočili?**

Priporočil bi uporabo javno-zasebnih ključev namesto gesel, kar je bistveno varnejše. Implementiral bi firewall pravila, ki omejujejo dostop do SSH samo iz določenih IP naslovov. Nastavil bi omejitev števila prijav z fail2ban ali podobnim orodjem. Omogočil bi 2FA za dodatno plast zaščite. Redno bi spremljal dnevnike prijav za odkrivanje sumljivih aktivnosti.

**Kako se spremeni rezultat, če uporabimo zelo močno geslo?**

Z uporabo zelo močnega gesla, na primer naključno generirane 20-znakovna kombinacija črk, številk in simbolov, postane brute force napad praktično neuporaben. Napadalec bi potreboval ogromno časa za ugotovitev takega gesla. Če geslo ni v wordlistu ali ni del slovarskih napadov, je verjetnost uspešnega napada minimalna. To je ključna razlika med šibkim geslom kot test123 in močnim geslom kot Xk9#mP2$qL@7zR4!nT8v.
