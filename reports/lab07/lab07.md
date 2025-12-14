# Lab07 - Izdelava lažne prijavne strani in phishing simulacija

## Analiza uspešnosti phishing napada

**Zakaj bi uporabnik padel na to prevaro?**

Lažna prijavna stran je bila izdelana tako, da vizualno posnema pravo targetirane prijavno stran. Uporabniki pogosto ne preverijo URL naslova in zaupajo izgledu strani. Če bi bila ta stran poslana preko phishing emaila z urgentnim sporočilom ("vaš račun bo blokiran"), bi bil uspeh napada verjetno večji.

**Elementi, ki povečujejo prepričljivost:**

- Vizualno podoben dizajn
- Uporaba logotipov in barv prave strani
- Preusmeritev na pravo stran po vnosu podatkov (uporabnik ne opazi, da je bil napaden)
- Uporaba SSL certifikata (če bi bilo v produkciji)

**Znaki, ki razkrijejo prevaro:**

- URL naslov ni pravi (moodle.fis.unm.si vs localhost ali druga domena)
- Manjkajoči SSL certifikat ali samopodpisan certifikat
- Manjkajoče dodatne funkcionalnosti (pozabljeno geslo, registracija)
- Drugačna domena v email naslovu

---

## Zaščita pred tovrstnimi napadi

**Kaj lahko naredimo kot uporabniki?**

Vedno preverjamo URL naslov v brskalniku. Preden vnesemo geslo, se prepričamo, da je naslov točno pravilen. Ne klikamo na povezave v sumljivih emailih, ampak gremo ročno na spletno stran. Uporabljamo 2FA, ki dodatno zaščiti račun, tudi če je geslo ukradeno.

**Kaj lahko naredijo organizacije?**

Organizacije lahko implementirajo DMARC, SPF in DKIM za preprečevanje ponarejanja emailov. Uporabljajo lahko tudi security awareness training za zaposlene, da prepoznajo phishing napade. Omogočajo naj 2FA za vse kritične sisteme in redno spremljajo nenavadno aktivnost.
