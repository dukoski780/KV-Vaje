# Lab02 - Varnost posameznikov v kibernetskem prostoru

## 2. Aktivnost: Analiza osebne izpostavljenosti

### Najdeni podatki:

**Osebni podatki:**
- Polno ime
- Osebni e-poštni naslov
- Telefonska številka (poslovna = osebna)
- Domači naslov (posloven sedež = domači naslov)

**Poslovni podatki:**
- Podjetje s.p.
- Poslovni sedež
- Kontaktni podatki

**Digitalni odtisi:**
- Pretekli projekti
- Objave in avtorstva
- Družbena omrežja (zaprta, a osnovni podatki vidni)

### Rezultati preverjanj:

**HaveIBeenPwned:**
```
Ni zaznanih vdorov z mojim e-poštnim naslovom
```

**Google Dorking:**
```
Ni najdenih izpostavljenih konfiguracijskih datotek ali občutljivih podatkov
```

---

## 3. Analiza in refleksija

### Ugotovitve

Analizo sem izvedel v incognito načinu, kjer sem s kombinacijo iskalnikov, osnovnih OSINT metod in orodij za preverjanje izpostavljenosti preveril, katere informacije o meni so javno dostopne. Želel sem ugotoviti, kako sem izpostavljen tako digitalno kot osebno.

Ugotovil sem, da se o meni na spletu pojavlja precej več podatkov, kot bi pričakoval. Najdene so bile informacije, kot so moje polno ime, osebni e-poštni naslov, podjetje in poslovni podatki s.p. Največja težava pa je, da je telefonska številka, ki je javno objavljena kot kontakt podjetja, tudi moja osebna številka, poslovni sedež podjetja pa je hkrati moj domači naslov. To pomeni, da sta osebni in poslovni identiteti popolnoma povezani, kar močno poveča tveganje socialnega inženiringa.

Na spletu se pojavljajo tudi pretekli projekti, objave in avtorstva, kar daje jasen vpogled v to, s čim se ukvarjam in v kakšnem okolju delam. Družbena omrežja so sicer zaprta, a osnovni podatki so kljub temu vidni.

Na tehnični strani nisem odkril večjih težav. Preverjanje s HaveIBeenPwned ni pokazalo, da bi bil moj e-poštni naslov vključen v kakšen vdor, Google dorking pa ni razkril nobenih izpostavljenih konfiguracijskih datotek ali občutljivih podatkov. To pomeni, da vsaj trenutno ni vidnih tehničnih ranljivosti. Kljub temu pa kombinacija javnega imena, emaila, telefona in naslova omogoča, da me nekdo zelo učinkovito cilja z napadi, ki temeljijo na zaupanju.

### Prepoznana tveganja

Največje tveganje sem prepoznal v tem, da lahko napadalec s temi podatki z lahkoto ustvari prepričljivo zgodbo. Če me nekdo pokliče na osebni telefon in omeni moj naslov ali podjetje, deluje bistveno bolj legitimno. Enako velja za lažna e-poštna sporočila, ki lahko izgledajo povsem pristna. Z javnim osebnim naslovom in telefonom je zloraba identitete veliko lažja, prav tako bi lahko nekdo v mojem imenu pošiljal lažne račune ali ponudbe. Zaradi javnega domačega naslova obstaja tudi vidik fizične izpostavljenosti.

**Ključna tveganja:**
- ️ **Socialni inženiring** - lahka manipulacija z uporabo osebnih podatkov
- ️ **Lažno predstavljanje** - lahko se izdajajo za mene (phishing, vishing)
- ️ **Ciljani napadi** - prepričljiva lažna sporočila/klici
- ️ **Finančna goljufija** - lažni računi v mojem imenu
- ️ **Fizična izpostavljenost** - znan domači naslov

### Črni scenarij

Da si lažje predstavljam tveganje, sem oblikoval črni scenarij. Napadalec najde moj naslov, telefon in podatke o podjetju ter me pokliče kot "bančni uslužbenec". Ker pozna moje podatke, mu hitro lahko začnem zaupati. Poskuša me prepričati v dejanje, ki bi mu omogočilo dostop do mojih računov ali do računalnika. Hkrati lahko moji stranki pošlje e-poštno sporočilo v mojem imenu in zahteva spremembo podatkov za nakazilo. Tak napad bi povzročil finančno, osebno in reputacijsko škodo.

### Ocena osebne varnosti/zasebnosti

Ko ocenjujem svojo kibernetsko varnost, vidim, da tehnični del ni problematičen. Največji problem je izpostavljenost osebnih kontaktnih podatkov, predvsem telefonske številke in domačega naslova. Ko sta oba povezana z mojo poslovno identiteto, postanem preprosta tarča socialnega inženiringa.

### Zaključek

Analiza mi je pokazala, da za visoko izpostavljenost na spletu ni potrebno veliko podatkov. Že nekaj osnovnih javnih informacij lahko omogoči zelo usmerjene in učinkovite napade. Zato je pomembno, da se osebne podatke obravnava premišljeno in da je kibernetska varnost stalen proces, ne enkraten dogodek.
