# Lab15 - MITM napad na GPG ključe in Web of Trust



## Razmislek

**Zakaj GPG ne zazna MITM napada samodejno?**

GPG temelji na kriptografiji javnega ključa, kar pomeni, da lahko kdorkoli generira par ključev za katerokoli ime ali email. GPG ne more vedeti, kateri ključ je "pravi" brez dodatne informacije. Sistem zaupa uporabniku, da preveri pristnost ključa prek fingerprinta. GPG ne more sam razlikovati med pravim Bobovim ključem in Malloryjevim ključem, ki trdi, da pripada Bobu.

**Kaj je fingerprint in zakaj je pomemben?**

Fingerprint je kriptografska hash vrednost javnega ključa. Je edinstven za vsak ključ in ga ni mogoče ponarediti. Fingerprint deluje kot digitalni "prstni odtis" ključa. Preverjanje fingerprinta po varnem kanalu je edini način, da se prepričamo, da smo dobili pravi ključ in ne lažnega. Brez preverjanja fingerprinta smo ranljivi za MITM napade.

**Zakaj e-pošta ni varen kanal za izmenjavo ključev?**

E-pošta potuje čez več strežnikov in je lahko prestregana ali modificirana. Napadalec lahko prestregne email z javnim ključem in ga zamenja s svojim lastnim ključem. Prejemnik ne bo mogel vedeti, da je ključ bil zamenjan. Zato je potrebno fingerprint preveriti po neodvisnem varnem kanalu, kot je telefonski klic ali osebni sestanek.

**Kako Web of Trust zmanjša tveganje MITM napada?**

Web of Trust deluje na principu medsebojnega podpisovanja ključev. Če Alice zaupa Charlesu in Charles podpiše Bobov ključ, lahko Alice zaupa Bobovemu ključu tudi brez neposrednega preverjanja. To ustvarja mrežo zaupanja, kjer uporabniki preverijo in potrdijo drug drugega. Če se pojavi lažen ključ, ga člani mreže hitro odkrijejo, ker fingerprint ne bo ujemal. Čim več ljudi preveri in podpiše ključ, bolj je zaupanja vreden.

---

## Ključne ugotovitve

Javni ključ sam po sebi ne zagotavlja pristnosti. Fingerprint je edini zanesljiv način preverjanja ključa, preverjanje pa mora potekati po drugem varnem kanalu. Web of Trust ustvarja mrežo zaupanja med uporabniki. MITM napadi so možni, če ne preverimo fingerprinta.
