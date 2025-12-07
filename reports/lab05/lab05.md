# Lab05 - Socialni inženiring in obrambe pred njim

## Analiza phishing sporočila

**Prejeto sporočilo:**

```
From: martin@mdstaging.eu
To: martin@dukoski.si
Subject: Obvezna varnostna posodobitev računa

Spoštovani,

zaradi nadgradnje varnostnega sistema morate potrditi svoj račun
Microsoft 365. Če potrditve ne izvedete v naslednjih 6 urah, bo vaš
dostop začasno onemogočen.

🔒 Kliknite tukaj za preverjanje računa:
http://office365-security-check.com/login

Hvala za hitro ukrepanje.
Microsoft Security Team
```

**Opažene značilnosti phishing sporočila:**

- **Domena pošiljatelja:** martin@mdstaging.eu (ni povezana z Microsoftom)
- **Lažni link:** http://office365-security-check.com/login (ni uradna Microsoft domena)
- **Časovni pritisk:** "v naslednjih 6 urah" - tipična taktika socialnega inženiringa
- **Grožnja:** "dostop začasno onemogočen" - ustvarja strah
- **Generičen pozdrav:** "Spoštovani" namesto osebnega nagovora
- **Značilnosti sumljivosti:**
  - Microsoft uporablja domeno @microsoft.com ali @office365.com
  - Uradni Microsoft nikoli ne zahteva potrditve preko zunanjega linka
  - Uporaba emojia  v uradni komunikaciji je nenavadna

---

## Analiza headerjev

**Ključni deli headerja:**

```
From: martin@mdstaging.eu
To: martin@dukoski.si
Return-Path: <martin@mdstaging.eu>
DKIM-Signature: d=mdstaging.eu
Received: from rh8.neoserv.si
X-Sender: martin@mdstaging.eu
```

**Ugotovitve:**

- **IP pošiljatelja:** 152.89.234.128 (rh8-a.mail-neoserv.si)
- **Domena:** mdstaging.eu - ni povezana z Microsoft Corporation
- **DKIM:** Podpisan za mdstaging.eu (veljavno za to domeno, ampak to ni Microsoft)
- **Server:** Neoserv.si - slovenski gostitelj
- **Lokacija:** Slovenija

**DKIM/SPF rezultati:**

Email je tehnično veljaven za domeno mdstaging.eu, vendar ta domena ni Microsoft. To pomeni, da je email uspešno poslan iz te domene, ampak se lažno predstavlja kot Microsoft Security Team.

---

## Refleksija in analiza

**Kako hitro opazite sumljivost e-poštnega sporočila?**

Pri pozornem branju je sumljivost očitna takoj - predvsem domena pošiljatelja (mdstaging.eu namesto microsoft.com) in neuradna povezava. Če pa sem pod časovnim pritiskom ali utrujen, lahko hitro spregledaš te znake.

**Bi z zagotovostjo lahko vsako sporočilo prepoznali kot nevarno brez headerja?**

Ne, zagotovo ne. Brez pregleda headerjev se lahko osredotočim samo na vsebino in očitne napake. Naprednješi phishing napadi lahko vsebujejo manj očitnih znakov, zato je analiza headerjev kritičnega pomena.

**Kaj bi svetovali nekomu, ki je nov uporabnik elektronske pošte?**

- Nikoli ne vpisuj gesel preko linkov iz emailov
- Vedno preveri domeno pošiljatelja
- Če si negotov, pojdi na uradno stran ročno (vtipkaj URL v brskalnik)
- Pozornost na časovni pritisk in grožnje - to so znaki socialnega inženiringa
- Pri pomembnih zadevah preveri header sporočila

**Ali lahko iz headerja ugotovimo IP pošiljatelja in lokacijo?**

Da. V tem primeru:
- **Phishing email:** 152.89.234.128 (Slovenija, Neoserv hosting)
- **Legitimen Moodle email:** 178.172.53.239 (Slovenija, FIŠ UNM)

**So v headerju vidni znaki preusmeritev preko več strežnikov?**

Da, vsak "Received:" zapis predstavlja en korak od strežnika do strežnika. Normalno je, da je več vrstic. Sumljivo postane, če:
- Je dolga veriga različnih, neznanih domen
- So prisotni veliki geografski skoki
- So velike časovne razlike med koraki

**So prisotne napake SPF/DKIM/DMARC?**

Pri phishing emailu so SPF/DKIM tehnično veljavni za domeno mdstaging.eu, vendar to ni Microsoft. Email je legitimno poslan iz te domene, ampak se lažno predstavlja kot nekdo drug.

Pri legitimnem Moodle emailu:
- spf=pass
- dkim=pass
- dmarc=pass

Vse preverjanje je uspešno in domena se ujema s pošiljateljem.
