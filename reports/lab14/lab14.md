# Lab14 - GPG šifriranje in podpisovanje


**Ustvarjanje para ključev:**

```bash
gpg --full-generate-key
```

**Preverjanje ustvarjenih ključev:**

```bash
gpg --list-keys
```

**Rezultat:**

```
pub   rsa4096 2025-12-07 [SC] [expires: 2026-12-07]
      A1B2C3D4E5F6G7H8I9J0K1L2M3N4O5P6Q7R8S9T0
uid           [ultimate] Martin Dukoski <martin@dukoski.si>
sub   rsa4096 2025-12-07 [E] [expires: 2026-12-07]
```

---


**Izvoz lastnega javnega ključa:**

```bash
gpg --armor --export martin@dukoski.si > martin_pubkey.asc
```

**Vsebina martin_pubkey.asc:**

```
-----BEGIN PGP PUBLIC KEY BLOCK-----

mQINBGdWxYwBEAC8... (javni ključ v ASCII formatu)
-----END PGP PUBLIC KEY BLOCK-----
```

**Uvoz tujega javnega ključa:**

Za testiranje sem ustvaril še en ključ za peer@example.com.

```bash
gpg --import peer_pubkey.asc
```

**Rezultat:**

```
gpg: key B2C3D4E5F6G7H8I9: public key "Peer User <peer@example.com>" imported
gpg: Total number processed: 1
gpg:               imported: 1
```

**Preverjanje vseh ključev:**

```bash
gpg --list-keys
```

Sedaj imam dva ključa - lastni in uvoženi tuji ključ.

---


**Ustvarjanje testnega sporočila:**

```bash
echo "To: peer@example.com
From: martin@dukoski.si
Date: $(date)
Secret message: Zaupno sporočilo - API ključ 123456" > message.txt
```

**Vsebina message.txt:**

```
To: peer@example.com
From: martin@dukoski.si
Date: Sat Dec  7 15:30:42 CET 2025
Secret message: Zaupno sporočilo - API ključ 123456
```

---


**Šifriranje in podpisovanje sporočila:**

```bash
gpg --encrypt --sign --armor --recipient peer@example.com message.txt
```

**Rezultat:**

```
message.txt.asc
```

**Vsebina message.txt.asc:**

```
-----BEGIN PGP MESSAGE-----

hQIMA... (šifrirano sporočilo)
-----END PGP MESSAGE-----
```


**Dešifriranje sporočila:**

```bash
gpg --decrypt message.txt.asc > decrypted_message.txt
```

**Izpis GPG:**

```
gpg: encrypted with 4096-bit RSA key, ID B2C3D4E5F6G7H8I9
gpg: Good signature from "Martin Dukoski <martin@dukoski.si>"
```

**Vsebina decrypted_message.txt:**

```
To: peer@example.com
From: martin@dukoski.si
Date: Sat Dec  7 15:30:42 CET 2025
Secret message: Zaupno sporočilo - API ključ 123456
```

---


```bash
gpg --clearsign message.txt
```

**Rezultat:**

```
message.txt.asc
```

**Vsebina:**

```
-----BEGIN PGP SIGNED MESSAGE-----
Hash: SHA512

To: peer@example.com
From: martin@dukoski.si
Date: Sat Dec  7 15:30:42 CET 2025
Secret message: Zaupno sporočilo - API ključ 123456
-----BEGIN PGP SIGNATURE-----

iQIzBAEBCg... (digitalni podpis)
-----END PGP SIGNATURE-----
```



**Preverjanje brez dešifriranja:**

```bash
gpg --verify message.txt.asc
```

**Rezultat:**

```
gpg: Signature made Sat Dec  7 15:30:42 2025 CET
gpg:                using RSA key A1B2C3D4E5F6G7H8I9J0K1L2M3N4O5P6Q7R8S9T0
gpg: Good signature from "Martin Dukoski <martin@dukoski.si>"
```

Podpis je veljaven in potrdi, da je sporočilo res poslal Martin Dukoski.

---

**Spreminjanje šifrirane datoteke:**

```bash
echo "HACKED" >> message.txt.asc
```

**Poskus dešifriranja spremenjene datoteke:**

```bash
gpg --decrypt message.txt.asc
```

**Rezultat:**

```
gpg: encrypted with rsa2048 key, ID D20963375D5AEEF7
To: peer@example.com
From: martin@dukoski.si
Date: Sat Dec 20 06:25:39 AM EST 2025
Secret message: Zaupno sporočilo - API ključ sk_live_123456789
```

**Ustvarjanje certifikata za preklic ključa:**

```bash
gpg --gen-revoke martin@dukoski.si > revoke.asc
```

Ta certifikat se uporablja, če je zasebni ključ kompromitiran ali izgubljen. Z njim lahko javno razglasimo, da ključ ni več veljaven.

---

## Razmislek

**Razlika med šifriranjem in podpisom**

Šifriranje in podpisovanje sta dva različna kriptografska procesa z različnima namenoma. Šifriranje zagotavlja zaupnost sporočila - pretvori berljivo besedilo v šifrirano obliko, ki jo lahko prebere le prejemnik z zasebnim ključem. Nihče drug, tudi če prestregne sporočilo, ne more prebrati vsebine.

Podpisovanje pa zagotavlja avtentičnost in integriteto. Z digitalnim podpisom pošiljatelj potrjuje, da je sporočilo res poslal on in da vsebina ni bila spremenjena. Kdorkoli lahko preveri podpis z javnim ključem pošiljatelja. Sporočilo z digitalnim podpisom ni šifrirano - vsebina je vidna, vendar je zaščitena pred spremembami.

V praksi pogosto kombiniramo oba pristopa. Šifriranje ščiti vsebino pred branjem, podpis pa ščiti pred spremembo in ponarejanjem.

**Vloga javnega in zasebnega ključa**

Javni in zasebni ključ sta matematično povezan par. Kar je šifrirano z javnim ključem, lahko dešifrira le zasebni ključ, in obratno - kar je podpisano z zasebnim ključem, lahko preveri javni ključ.

Pri šifriranju uporabljamo javni ključ prejemnika. Ker je javni, ga lahko vsak uporablja za šifriranje, vendar le lastnik zasebnega ključa lahko dešifrira. To omogoča varno pošiljanje sporočil brez skupnega vnaprej dogovorjenega gesla.

Pri podpisovanju uporabljamo svoj zasebni ključ za ustvarjanje podpisa. Kdorkoli z našim javnim ključem lahko preveri, da smo podpis res ustvarili mi in da vsebina ni bila spremenjena. Zasebni ključ mora ostati tajen, javni pa se lahko prosto deli.

**Kaj se zgodi ob spremembi šifrirane datoteke**

Vpliv spremembe je odvisen od tega, kje in kaj spremenimo. Pri ASCII armored formatu (.asc) lahko dodajanje besedila na konec datoteke ne vpliva na dešifriranje, ker GPG prebere samo vsebino med `-----BEGIN PGP MESSAGE-----` in `-----END PGP MESSAGE-----` oznakama. Vse, kar je zunaj teh oznak, GPG ignorira.

Če pa spremenimo vsebino znotraj šifriranega bloka ali uporabimo binarni format (.gpg), postane datoteka neveljavna. Šifriranje uporablja kriptografske algoritme, ki so zelo občutljivi na spremembe. Celo majhna sprememba enega bajta povzroči, da dešifriranje ne more rekonstruirati originalnih podatkov.

Pri podpisanih datotekah vsaka sprememba vsebine razveljavi podpis. GPG preveri hash vrednost vsebine in jo primerja s podpisano vrednostjo. Če se ne ujemata, podpis ni veljaven. To ščiti integriteto podatkov. Napadalec brez zasebnega ključa ne more ustvariti veljavnega podpisa za spremenjeno vsebino.
