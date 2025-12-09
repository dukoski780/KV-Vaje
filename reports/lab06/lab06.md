# Lab06 - Testiranje varnosti gesel z razbijanjem zgoščenih vrednosti

## Priprava okolja


**Priprava testnih gesel:**
```bash
touch gesla.txt
cat << 'EOF' > gesla.txt
admin123
sunshine
P@ssword!
Tr0p1c@lF1$h
correcthorsebatterystaple2025!
EOF
```


**Uporabljen ukaz:**
```bash
john --format=raw-md5 --wordlist=/usr/share/wordlists/rockyou.txt hashes.txt
```

**Rezultat:**
```
0:00:00:00 Starting a new session
0:00:00:00 Loaded a total of 5 password hashes
0:00:00:00 Proceeding with wordlist mode
0:00:00:00 + Cracked user1
0:00:00:00 + Cracked user2
0:00:00:01 + Cracked user3
0:00:00:03 Session completed
```

**Prikaz najdenih gesel:**
```bash
john --show --format=Raw-MD5 hashes.txt
```

**Najdena gesla:**
```
user1:admin123
user2:sunshine
user3:P@ssword!

3 password hashes cracked, 2 left
```

---

## Analiza rezultatov

**Katera gesla so bila najdena in kako hitro?**

Najdena so bila gesla admin123, sunshine in P@ssword!. Vsa tri so bila zlomljena v manj kot 1 sekundi, ker so prisotna v rockyou.txt wordlist datoteki.

**Katerega močnega gesla program ni našel? Zakaj?**

Program ni našel gesel Tr0p1c@lF1$h in correcthorsebatterystaple2025!. Razlog je preprost - ta gesla niso v rockyou.txt wordlist datoteki. Prvo uporablja netipične zamenjave znakov, drugo pa je dolga unikatna kombinacija besed, ki ne obstaja v znanih wordlistih.

---

## Vpliv dolžine gesla na varnost

**Kako se povečuje ocena varnosti, ko dodajate dolžino?**

Dolžina gesla je najpomembnejši dejavnik varnosti. Z vsakim dodatnim znakom se čas za lomljenje eksponentno poveča. Kratko 8-znakovno geslo lahko napadalec zlomi relativno hitro, medtem ko 14+ znakovno geslo predstavlja bistveno večji izziv. Tudi preprosta dolga besedna zveza je varnejša od kratkega gesla s simboli.

---

## Vpliv posebnih znakov

**Kako vplivajo posebni znaki na oceno?**

Posebni znaki tehnično povečajo prostor možnih kombinacij, vendar njihov učinek ni tako velik, kot bi si mislili. Večina uporabnikov jih uporablja na predvidljive načine - velika začetnica, končna številka in klicaj. Orodja za lomljenje gesel poznajo te vzorce in jih upoštevajo pri napadih. Resnično koristen je le poseben znak, ki je umeščen naključno v sredino gesla.

---

## Passphrase vs klasično geslo

**Kako se ocenjuje "passphrase" v primerjavi s klasičnim geslom?**

Passphrase uporablja več besed namesto kratkega zapletenega gesla. Prednost je očitna - veliko lažje si jo zapomnimo kot naključne znake, hkrati pa je dolga in zato varna. Pomembno je, da niso splošno znani citati ali fraze. Če vzamemo nekaj naključnih nesmiselnih besed in jih povežemo s simboli, dobimo zelo močno geslo, ki ga je težko razbiti.

---

## Priporočila za vsakodnevno uporabo

**Katero geslo bi priporočili za vsakodnevno uporabo in zakaj?**

Za vsakodnevno rabo priporočam kombinacijo več naključnih besed s simboli vmes, dolžine vsaj 16 znakov. Tako geslo je enostavno zapomnljivo in hkrati težko razbiti. Pomembno je, da je vsako geslo različno za vsak račun, kar pomeni, da je potreben password manager. Ročno si lahko zapomnimo le glavno geslo za manager, vsa ostala naj bodo generirana in shranjena.
