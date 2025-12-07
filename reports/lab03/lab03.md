# Lab03 - OSINT – Zbiranje informacij o posameznikih na spletu


## Priprava okolja


**Namestitev:**
```bash
sudo apt update
sudo apt install python3 python3-pip git -y

# Sherlock
cd ~
git clone https://github.com/sherlock-project/sherlock.git
cd sherlock
pip3 install -r requirements.txt

# Maigret
pip3 install maigret
```

---

## Testiranje

**Uporabljeni ukazi:**
```bash
# Sherlock
cd ~/sherlock
python3 -m sherlock_project elonmusk

# Maigret
maigret elonmusk
```

**Rezultati:**
- Sherlock: 42 najdenih profilov
- Maigret: 197 najdenih profilov

---

## Analiza in poročilo

Pri iskanju uporabniškega imena elonmusk sta obe orodji vrnili različne rezultate. Sherlock je našel precej manj profilov, Maigret pa občutno več, saj preverja širši nabor platform in zazna tudi variacije uporabniškega imena ter dodatne ID-je. Med rezultati sem opazil, da nekateri profili ne obstajajo več oziroma vrnejo napako, kar je pri obeh orodjih pričakovano.

Kar se tiče občutljivih podatkov, nisem našel e-poštnih naslovov ali telefonskih številk, so pa bili izpisani avatarji in povezave do profilnih slik. Povezovanje različnih aliasov je lahko občutljivo samo po sebi, zato bi oseba svoje podatke najlažje zaščitila tako, da loči uporabniška imena glede na namen, uporablja ločene e-poštne naslove in po možnosti izbriše stare, neaktivne račune. Kadar to ni mogoče, ostane možnost zahteve za izbris pri posamezni platformi.

---

## Refleksija in analiza

**Katere informacije so bile najlažje najdene? Katere je bilo najtežje najti?**

Najlažje je bilo najti informacije na večjih in dobro podprtih straneh, kjer orodji že poznata strukturo URL-jev. Težje je bilo najti podatke na manjših, lokalnih platformah ali tam, kjer uporabniško ime ni enako.

**Kako bi vi sami prilagodili svoje vedenje na spletu, potem ko ste izvedli to vajo?**

Po vaji bi sam bolj pazil, kako pogosto uporabljam enako uporabniško ime, ter bi ločil identitete glede na to, ali gre za osebne, službene ali manj pomembne registracije.

**Ali menite, da je uporaba OSINT orodij etično sporna? V katerih primerih je upravičena?**

Kar zadeva etičnost, menim, da so OSINT orodja lahko sporna, če se uporabljajo za nadlegovanje, profiliranje ali iskanje podatkov brez dovoljenja. Po drugi strani pa so povsem upravičena pri samopreizkusu, varnostnem testiranju z dovoljenjem ali pri digitalni forenziki, kjer pomagajo razumeti potek incidenta.

---
