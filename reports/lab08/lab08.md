# Lab08 - Uporaba varne komunikacije

## Refleksija

**Kako bi razložili razliko med nešifriranim in šifriranim sporočilom? Katere podatke lahko napadalec vidi v prvem primeru in katere v drugem?**

Razlika je v tem, da je sporočilo lahko šifrirano ali ne. Pri nešifriranem SMTP prometu napadalec v Wiresharku vidi vse podatke - SMTP ukaze, naslove pošiljatelja in prejemnika, zadevo ter celotno vsebino sporočila. Pri šifriranem SMTP s TLS pa napadalec vidi samo, da je komunikacija potekala, vidni so IP naslovi in čas, vendar ne more prebrati vsebine.

**Zakaj je preverjanje fingerprinta pri PGP pomembno za preprečitev man-in-the-middle napada?**

Javni ključ, ki smo ga prejeli, lahko pripada napačni osebi. Fingerprint povezuje ključ s pravo osebo. Napadalec lahko ponaredi ime pošiljatelja, email naslov in videz sporočila, ne more pa ustvariti lažnega ključa z enakim fingerprintom kot originalni ključ. Preverjanje fingerprinta po varnem kanalu razbije tiho podtikanje lažnega javnega ključa.

**Kdaj bi uporabili PGP in kdaj Signal?**

PGP bi uporabili pri daljši in bolj obsežni komunikaciji, predvsem za šifriranje elektronske pošte, podpisovanje dokumentov in arhiviranje. Signal pa pri hitri, vsakodnevni komunikaciji v realnem času, kot so pogovori, klici in video konference. PGP zahteva ročno upravljanje ključev, Signal pa deluje avtomatično in je enostavnejši za uporabo.

**Ali menite, da bi moralo biti end-to-end šifriranje privzeto v vseh komunikacijskih aplikacijah?**

Z vidika varnosti in zasebnosti da, z vidika uporabniške izkušnje pa ne nujno. E2E šifriranje ščiti pred notranjimi zlorabami pri ponudniku, množičnim nadzorom in naredi strežnike manj zanimive tarče za napade. Lahko pa povzroči počasnejše delovanje in težave pri sinhronizaciji med napravami. Če ne gre za občutljive podatke, ni nujno potrebno. Če pa gre za občutljivo komunikacijo, bi moralo biti privzeto vključeno.
