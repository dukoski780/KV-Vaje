# Lab16 - Secrets Management z GPG


## Razmislek

**Zakaj skrivnosti ne sodijo v izvorno kodo?**

Skrivnosti, kot so gesla, API ključi in tokeni, predstavljajo občutljiv del informacijskih sistemov. V praksi se pogosto pojavljajo v izvorni kodi ali konfiguracijskih datotekah v Git repozitorijih. To je problematično, ker Git zgodovina ostane trajno shranjena - tudi če skrivnost izbrišemo, je še vedno dostopna v prejšnjih commitih.

Repozitoriji so dostopni več razvijalcem, avtomatiziranim sistemom in zunanjim orodjem. Vsak dodatni dostop povečuje napadalno površino. Osnovno varnostno pravilo je, da skrivnosti ne sodijo v izvorno kodo, temveč morajo biti ločene in zaščitene.

**Kakšna je razlika med simetričnim in asimetričnim šifriranjem skrivnosti?**

Simetrično šifriranje uporablja eno geslo za šifriranje in dešifriranje. Enostaven pristop, vendar prinaša težavo varnega posredovanja gesla. Če geslo pride v napačne roke, so vsi podatki ogroženi.

Asimetrično šifriranje uporablja par ključev - javni za šifriranje in zasebni za dešifriranje. Javni ključ se lahko varno deli, zasebni pa ostane samo pri lastniku. Ta pristop je varnejši za okolja z več uporabniki.

**Kaj se zgodi, če izgubimo zasebni ključ?**

Če zasebni ključ izgubimo brez varnostne kopije, do šifriranih podatkov ni več dostopa. Kriptografija nima "zadnjih vrat" - brez ključa podatkov ni mogoče obnoviti. Izguba ključa pomeni izgubo podatkov. Zato je potrebno zasebne ključe varnostno kopirati v šifrirani obliki na ločenih lokacijah.

**Kako bi to rešili v večjem podjetju?**

GPG je praktičen način za spoznavanje osnov upravljanja skrivnosti. Omogoča simetrično in asimetrično šifriranje ter pokaže, kako zaščititi občutljive podatke brez kompleksnih rešitev.

V večjih organizacijah se uporabljajo specializirana orodja, kot so HashiCorp Vault, AWS Secrets Manager ali Azure Key Vault. Ta omogočajo centralizirano upravljanje, nadzor dostopa, avtomatizirano rotacijo ključev in revizijske sledi.

Učinkovito upravljanje skrivnosti je temelj varne programske opreme. GPG dobro ponazori ključne koncepte: ločevanje skrivnosti od kode, uporabo šifriranja in pravilno upravljanje ključev. Ti osnovi so nujni za delo z naprednejšimi sistemi v produkcijskih okoljih.

---


Ključne ugotovitve:
- Skrivnosti nikoli ne shranjuj v nešifrirani obliki v Git
- Simetrično šifriranje je enostavno, asimetrično je varnejše
- Vedno odstrani dešifrirane datoteke po uporabi
- Za produkcijo uporabi specializirana orodja (Vault, Secrets Manager)
